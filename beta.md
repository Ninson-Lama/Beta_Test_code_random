export const __webpack_id__ = "brave_browser_resources_brave_new_tab_page_refresh_components_news_news_feed_tsx";
export const __webpack_ids__ = ["brave_browser_resources_brave_new_tab_page_refresh_components_news_news_feed_tsx"];
export const __webpack_modules__ = {
    "../../../brave/browser/resources/brave_new_tab_page_refresh/components/news/news_feed.tsx": (e, t, n) => {
        n.r(t),
        n.d(t, {
            NewsFeed: () => De,
            default: () => Ye
        });
        var r = n("../../../brave/node_modules/react/index.js")
          , o = n("../../../brave/components/brave_news/browser/resources/shared/Context.tsx")
          , a = n("../../../brave/node_modules/styled-components/dist/styled-components.esm.js")
          , i = n("../../../brave/node_modules/@brave/leo/react/button.js")
          , l = n("../../../brave/node_modules/@brave/leo/tokens/css/variables.js")
          , s = n("../../../brave/components/common/SecureLink.tsx")
          , c = n("../../../brave/components/common/locale.ts")
          , d = n("./brave/components/brave_news/common/brave_news.mojom.m.js");
        class m {
            constructor(e, t, n) {
                this.timerId = void 0,
                this.viewTimeMs = 0,
                this.handleVisibility = () => {
                    "visible" === document.visibilityState && this.isIntersecting ? this.timerId || this.startWaiting() : this.resetTimer()
                }
                ,
                this.element = n,
                this.onTimerExpired = e,
                this.viewTimeMs = t,
                this.isIntersecting = !n,
                n && (this.intersectionObserver = new IntersectionObserver((e => {
                    this.isIntersecting = e.some((e => e.isIntersecting)),
                    this.handleVisibility()
                }
                ),{
                    threshold: .5
                }))
            }
            startTracking() {
                document.addEventListener("visiblitychange", this.handleVisibility),
                this.intersectionObserver && this.element && this.intersectionObserver.observe(this.element),
                this.handleVisibility()
            }
            stopTracking() {
                this.resetTimer(),
                document.removeEventListener("visiblitychange", this.handleVisibility),
                this.intersectionObserver && this.element && this.intersectionObserver.unobserve(this.element)
            }
            startWaiting() {
                this.timerId || (this.timerId = window.setTimeout(( () => {
                    this.stopTracking(),
                    this.onTimerExpired()
                }
                ), this.viewTimeMs))
            }
            resetTimer() {
                window.clearTimeout(this.timerId),
                this.timerId = void 0
            }
        }
        var u = n("../../../brave/components/brave_news/browser/resources/shared/api.ts")
          , p = n("../../../brave/components/brave_news/browser/resources/shared/Icons.tsx")
          , g = n("../../../brave/components/common/Flex.tsx")
          , v = n("../../../brave/node_modules/@brave/leo/react/buttonMenu.js")
          , b = n("../../../brave/node_modules/@brave/leo/react/icon.js")
          , h = n("../../../brave/components/brave_news/browser/resources/shared/channel.ts");
        const f = new Intl.RelativeTimeFormat(void 0,{
            numeric: "auto"
        })
          , E = 36e5
          , w = 24 * E
          , y = {
            second: 1e3,
            minute: 6e4,
            hour: E,
            day: w,
            week: 7 * w,
            year: 365 * w
        }
          , _ = e => {
            var t;
            const n = Date.now()
              , r = new Date(e).getTime() - n
              , [o,a] = null !== (t = Object.entries(y).findLast(( ([,e]) => Math.abs(r) > e))) && void 0 !== t ? t : ["second", 1e3]
              , i = Math.floor(r / a);
            return {
                formatted: f.format(i, o),
                updatesIn: Math.max(6e5, a - Math.abs(r - i))
            }
        }
        ;
        var x = n("../../../brave/components/common/mojomUtils.ts");
        const C = (0,
        a.Ay)(i.A).withConfig({
            displayName: "MenuButton",
            componentId: "sc-q4nzob"
        })`
  --leo-button-padding: 0;

  flex-grow: 0;
`
          , A = a.Ay.h4.withConfig({
            displayName: "MetaInfoContainer",
            componentId: "sc-1vfhvmp"
        })`
  --leo-icon-size: 12px;

  margin: 0;

  font: ${l.gx.xSmall.regular};
  color: var(--bn-glass-50);

  display: flex;
  align-items: center;
  gap: ${l.YK.s};
`
          , N = e => e.publisherName ? e.publisherName : new URL(e.url.url).hostname;
        function I(e) {
            var t;
            const n = function(e) {
                const [t,n] = (0,
                r.useState)("");
                return (0,
                r.useEffect)(( () => {
                    if (!e)
                        return;
                    let t;
                    const r = () => {
                        const {formatted: o, updatesIn: a} = _(e);
                        n(o),
                        t = setTimeout(r, a)
                    }
                    ;
                    return r(),
                    () => {
                        clearTimeout(t)
                    }
                }
                ), [e]),
                t
            }((0,
            x.$F)(e.article.publishTime))
              , o = !e.hideChannel && r.createElement(r.Fragment, null, "• ", null !== (t = p.GH[e.article.categoryName]) && void 0 !== t ? t : p.GH.default, " ", (0,
            h.J)(e.article.categoryName));
            return r.createElement(A, null, N(e.article), " ", o, " • ", n)
        }
        function k(e) {
            return r.createElement(g.A, {
                direction: "row",
                justify: "space-between",
                align: "center"
            }, r.createElement(I, {
                ...e
            }), r.createElement(v.A, null, r.createElement(C, {
                slot: "anchor-content",
                kind: "plain-faint",
                size: "tiny"
            }, r.createElement(b.Ay, {
                name: "more-horizontal"
            })), r.createElement("leo-menu-item", {
                onClick: t => {
                    (0,
                    u.Ay$)().setPublisherPref(e.article.publisherId, u.VvM.DISABLED),
                    t.stopPropagation()
                }
            }, (0,
            c.OE)("BRAVE_NEWS_HIDE_CONTENT_FROM", {
                $1: N(e.article)
            }))))
        }
        var $ = n("../../../brave/components/brave_news/browser/resources/feed/Card.tsx");
        const S = (0,
        a.Ay)($.Ay).withConfig({
            displayName: "Container",
            componentId: "sc-1bwfx6b"
        })`
  display: flex;
  flex-direction: column;
  gap: ${l.YK.m}
`
          , T = a.Ay.a.withConfig({
            displayName: "BatAdLabel",
            componentId: "sc-17seix"
        })`
  padding: 0 2px;

  border: 1px solid rgba(var(--bn-text-base), 0.3);
  border-radius: 3px;

  text-decoration: none;

  color: rgba(var(--bn-text-base, 0.7));
  font: ${l.gx.small.regular};
  line-height: 16px;
`
          , R = (0,
        a.Ay)(i.A).withConfig({
            displayName: "CtaButton",
            componentId: "sc-qzoes"
        })`
  --leo-button-color: var(--bn-glass-container);
  align-self: flex-start;
`
          , K = (0,
        a.Ay)($.v1).withConfig({
            displayName: "AdImage",
            componentId: "sc-52rwnr"
        })`
  height: unset;
`
          , O = (e, t) => {
            const [n,o] = r.useState(null)
              , a = r.useRef();
            return a.current = e,
            r.useEffect(( () => {
                if (!n)
                    return;
                const e = new m(( () => {
                    var e;
                    null === (e = a.current) || void 0 === e || e.call(a)
                }
                ),t,n);
                return e.startTracking(),
                () => {
                    e.stopTracking()
                }
            }
            ), [n, t, e]),
            {
                setEl: o
            }
        }
          , B = ["https:", "chrome:", "brave:"];
        function F(e) {
            var t, n, a, i;
            const [l,d] = r.useState(void 0)
              , m = null !== (i = null !== (n = null === (t = null == l ? void 0 : l.image.paddedImageUrl) || void 0 === t ? void 0 : t.url) && void 0 !== n ? n : null === (a = null == l ? void 0 : l.image.imageUrl) || void 0 === a ? void 0 : a.url) && void 0 !== i ? i : ""
              , {openArticlesInNewTab: p} = (0,
            o.D5)()
              , g = r.useCallback(( () => {
                l && (console.debug(`Brave News: Viewed display ad: ${l.uuid}`),
                (0,
                u.Ay$)().onDisplayAdView(l.uuid, l.creativeInstanceId))
            }
            ), [l])
              , {setEl: v} = O(g, 1e3)
              , b = r.useCallback((async e => {
                l && (console.debug(`Brave News: Visited display ad: ${l.uuid}`),
                await (0,
                u.Ay$)().onDisplayAdVisit(l.uuid, l.creativeInstanceId),
                (0,
                $.Ql)(l.targetUrl.url, B)(e))
            }
            ), [l])
              , {setElementRef: h} = function(e, t) {
                const n = r.useRef();
                n.current = e;
                const {visible: o, setElementRef: a} = function(e) {
                    const [t,n] = r.useState(!1)
                      , [o,a] = r.useState(null);
                    return r.useEffect(( () => {
                        if (!o)
                            return;
                        const t = new IntersectionObserver(( ([e]) => {
                            e.isIntersecting && n(!0)
                        }
                        ),{
                            root: e.rootElement,
                            rootMargin: e.rootMargin,
                            threshold: e.threshold
                        });
                        return t.observe(o),
                        () => {
                            t.disconnect()
                        }
                    }
                    ), [e.rootElement, o]),
                    {
                        visible: t,
                        setElementRef: a
                    }
                }(t);
                return r.useEffect(( () => {
                    var e;
                    o && (null === (e = n.current) || void 0 === e || e.call(n))
                }
                ), [o]),
                {
                    setElementRef: a
                }
            }((async () => {
                console.debug("Brave News: Fetching an advertisement");
                const e = await (0,
                u.Ay$)().getDisplayAd().then((e => e.ad));
                d(null != e ? e : null)
            }
            ), {
                rootMargin: "0px 0px 1000px 0px"
            });
            return null === l ? null : l ? r.createElement(S, {
                ref: v,
                onClick: b
            }, r.createElement(K, {
                loading: "eager",
                src: m
            }), r.createElement(A, null, r.createElement(T, {
                onClick: e => e.stopPropagation(),
                target: p ? "_blank" : void 0,
                href: "chrome://rewards"
            }, (0,
            c.JK)("BRAVE_NEWS_ADVERT_BADGE")), "•", " " + l.description), r.createElement($.hE, null, r.createElement(s.Ay, {
                allowedSchemes: B,
                href: l.targetUrl.url,
                onClick: e => {
                    e.preventDefault()
                }
            }, l.title)), r.createElement(R, {
                kind: "filled"
            }, l.ctaText)) : r.createElement("div", {
                ref: h
            })
        }
        const z = (0,
        a.Ay)($.Ay).withConfig({
            displayName: "Container",
            componentId: "sc-1hssqp2"
        })`
  display: flex;
  flex-direction: column;
  gap: ${l.YK.s};
  padding-top: ${l.YK.l};
`;
        function j({info: e, hideChannel: t, feedDepth: n}) {
            var a, i, s, c;
            const {reportVisit: d} = (0,
            o.D5)()
              , m = e.data.url.url;
            return r.createElement(z, {
                onClick: e => {
                    (0,
                    $.Ql)(m)(e),
                    void 0 !== n && d(n)
                }
            }, r.createElement(k, {
                article: e.data,
                hideChannel: t
            }), r.createElement(g.A, {
                direction: "row",
                gap: l.YK.xl,
                justify: "space-between",
                align: "start"
            }, r.createElement($.hE, null, r.createElement($.Sx, {
                href: m,
                feedDepth: n
            }, e.data.title)), r.createElement($.v5, {
                loading: "lazy",
                src: null !== (c = null !== (i = null === (a = e.data.image.paddedImageUrl) || void 0 === a ? void 0 : a.url) && void 0 !== i ? i : null === (s = e.data.image.imageUrl) || void 0 === s ? void 0 : s.url) && void 0 !== c ? c : ""
            })))
        }
        const V = (0,
        a.Ay)(g.A).withConfig({
            displayName: "Container",
            componentId: "sc-psu4ko"
        })`
  color: var(--bn-glass-50);
  gap: ${l.YK.xl};

  & > hr {
    flex: 1;
    border-color: var(--bn-glass-10);
  }
`;
        function D() {
            return r.createElement(V, {
                align: "center",
                justify: "stretch"
            }, r.createElement("hr", null), r.createElement(g.A, {
                align: "center",
                gap: 6
            }, r.createElement(b.Ay, {
                name: "check-circle-outline"
            }), " ", r.createElement("span", null, (0,
            c.JK)("BRAVE_NEWS_CAUGHT_UP"))), r.createElement("hr", null))
        }
        const Y = (0,
        a.Ay)($.Ay).withConfig({
            displayName: "Container",
            componentId: "sc-18gww0f"
        })`
  display: flex;
  flex-direction: column;
  gap: ${l.YK.l};

  & > ${$.hE} {
    --leo-icon-color: currentColor;
    --leo-icon-size: ${l.Kk.s};

    gap: ${l.YK.m};
    align-items: center;

    margin: ${l.YK.m} 0;
  }

  & > ${$.Ay} {
    border-radius: ${l.r8.m};
  }
`;
        function L({info: e, feedDepth: t}) {
            var n;
            const o = e.type === d.JYA.CHANNEL ? (0,
            h.J)(e.id) : e.id;
            return r.createElement(Y, null, r.createElement($.hE, null, null !== (n = p.GH[e.id]) && void 0 !== n ? n : p.GH.default, " ", o), e.articles.map(( (e, n) => {
                const o = e.article || e.hero;
                return r.createElement(j, {
                    key: n,
                    info: o,
                    hideChannel: o.type === d.JYA.CHANNEL,
                    feedDepth: void 0 === t ? void 0 : t + n
                })
            }
            )))
        }
        var M = n("../../../brave/components/brave_news/browser/resources/shared/PublisherCard.tsx");
        const W = a.Ay.div.withConfig({
            displayName: "Row",
            componentId: "sc-142dcuj"
        })`
  display: grid;
  grid-template-columns: repeat(3, minmax(0, 1fr));
  gap: ${l.YK["2Xl"]};
  margin-top: ${l.YK.m};
`
          , H = (0,
        a.Ay)(b.Ay).withConfig({
            displayName: "TitleIcon",
            componentId: "sc-a6ogig"
        })`
  --leo-icon-size: ${l.Kk.s};
  margin-right: ${l.YK.s};
`
          , U = (0,
        a.Ay)($.Ay).withConfig({
            displayName: "Container",
            componentId: "sc-5w4a2g"
        })`
  padding: ${l.YK["2Xl"]} ${l.YK.xl};
`;
        function P({info: e}) {
            return r.createElement(U, null, r.createElement($.hE, null, r.createElement(H, {
                name: "star-outline"
            }), (0,
            c.JK)("BRAVE_NEWS_SOURCES_RECOMMENDATION")), r.createElement(W, null, e.publisherIds.map((e => r.createElement(M.A, {
                key: e,
                publisherId: e
            })))))
        }
        const J = (0,
        a.Ay)($.Ay).withConfig({
            displayName: "Container",
            componentId: "sc-1t69mjo"
        })`
  display: flex;
  flex-direction: column;
  gap: ${l.YK.s};

  & > ${$.v1} {
    margin-bottom: ${l.YK.l};
  }
`;
        function G({info: e, feedDepth: t}) {
            var n, a, i, l;
            const {reportVisit: s} = (0,
            o.D5)();
            return r.createElement(J, {
                onClick: n => {
                    (0,
                    $.Ql)(e.data.url.url)(n),
                    void 0 !== t && s(t)
                }
            }, r.createElement($.v1, {
                loading: "lazy",
                src: null !== (l = null !== (a = null === (n = e.data.image.paddedImageUrl) || void 0 === n ? void 0 : n.url) && void 0 !== a ? a : null === (i = e.data.image.imageUrl) || void 0 === i ? void 0 : i.url) && void 0 !== l ? l : ""
            }), r.createElement(k, {
                article: e.data
            }), r.createElement($.hE, null, r.createElement($.Sx, {
                href: e.data.url.url,
                feedDepth: t
            }, e.data.title)))
        }
        var q = n("../../../brave/node_modules/@brave/leo/react/progressRing.js");
        const X = (0,
        a.Ay)($.Ay).withConfig({
            displayName: "Container",
            componentId: "sc-sgpxzl"
        })`
  display: flex;
  align-items: center;
  justify-content: center;
`
          , Q = (0,
        a.Ay)(q.A).withConfig({
            displayName: "Spinner",
            componentId: "sc-yvfsrp"
        })`
  --leo-progressring-color: var(--bn-glass-25);
`;
        function Z() {
            return r.createElement(X, null, r.createElement(Q, null))
        }
        const ee = (0,
        a.Ay)(g.A).withConfig({
            displayName: "Container",
            componentId: "sc-busa4j"
        })`
  text-align: center;

  padding: ${l.YK["3Xl"]};
  gap: ${l.YK.m};
  color: var(--bn-glass-70);

  & > svg {
    margin-bottom: ${l.YK["2Xl"]};
    fill: none;
  }

  & > leo-button {
    flex: 0;
  }
`
          , te = (0,
        a.Ay)(i.A).withConfig({
            componentId: "sc-za2nq9"
        })`
  --leo-button-color: var(--bn-glass-10);

  border-radius: 20px;
  overflow: hidden;
  backdrop-filter: brightness(0.8) blur(32px);
`
          , ne = (0,
        a.Ay)(g.A).withConfig({
            displayName: "Container",
            componentId: "sc-zrvjr3"
        })`
  text-align: center;

  padding: ${l.YK["3Xl"]};
  gap: ${l.YK.m};
  color: var(--bn-glass-70);

  & > svg {
    margin-bottom: ${l.YK.xl};
    fill: none;
  }
`
          , re = e => {
            const t = {
                ..."object" == typeof history.state ? history.state : {},
                ...e
            };
            history.replaceState(t, document.title)
        }
          , oe = (e, t) => {
            var n;
            const r = null !== (n = history.state) && void 0 !== n ? n : {};
            return e in r ? r[e] : t
        }
          , ae = (0,
        a.Ay)(g.A).withConfig({
            displayName: "Container",
            componentId: "sc-2in3a2"
        })`
  text-align: center;

  padding: ${l.YK["3Xl"]};
  gap: ${l.YK.m};
  color: var(--bn-glass-70);

  & > svg {
    margin-bottom: ${l.YK.xl};
    fill: none;
  }
`
          , ie = "feed-card"
          , le = a.Ay.div.withConfig({
            displayName: "FeedContainer",
            componentId: "sc-1umnda5"
        })`
  width: 540px;
  display: flex;
  flex-direction: column;
  gap: ${l.YK.xl};

  /* Hide Ad elements, if we weren't able to fill them */
  & .${ie}:empty {
    display: none;
  }
`
          , se = (e, t) => {
            if (e.advert)
                return t;
            if (e.article)
                return e.article.data.url.url;
            if (e.hero)
                return e.hero.data.url.url;
            if (e.cluster)
                return t;
            if (e.discover)
                return t;
            throw new Error("Unsupported FeedItem!")
        }
          , ce = "news-feed"
          , de = 25
          , me = "bn-scroll-data"
          , ue = "bn-card-count"
          , pe = "data-news-card-count"
          , ge = 36e5
          , ve = e => () => {
            var t;
            re({
                [me]: {
                    itemId: e,
                    innerWidth: window.innerWidth,
                    innerHeight: window.innerHeight,
                    scrollPos: null === (t = document.scrollingElement) || void 0 === t ? void 0 : t.scrollTop
                }
            })
        }
          , be = {
            [d.HLt.ConnectionError]: r.createElement((function() {
                const {refreshFeedV2: e} = (0,
                o.D5)();
                return r.createElement(ae, {
                    align: "center",
                    direction: "column",
                    justify: "center",
                    gap: l.YK.m
                }, r.createElement("svg", {
                    xmlns: "http://www.w3.org/2000/svg",
                    fill: "none",
                    width: "99",
                    viewBox: "0 0 64 46"
                }, r.createElement("path", {
                    fill: "#F0F2FF",
                    fillRule: "evenodd",
                    d: "M49.67 46H13.33C5.36 46 0 41.32 0 34.37c0-5.45 3.08-10.33 7.84-12.74l-.02-.84C7.82 9.69 16.92.67 28.1.67a20.3 20.3 0 0118.37 11.65c9.74.4 17.54 8.4 17.54 18.17C64 39.33 57.84 46 49.67 46zm-3.98-28.37c-.24 0-.47.02-.7.05-1.24.14-2.4-.6-2.81-1.77A14.94 14.94 0 0028.08 6a14.88 14.88 0 00-14.92 14.79c0 .68.06 1.37.18 2.11a2.67 2.67 0 01-1.8 2.96 8.95 8.95 0 00-6.2 8.5c0 5.85 6.12 6.3 8 6.3h36.33c4.47 0 9-3.5 9-10.17 0-7.1-5.83-12.86-12.98-12.86zM40 35.33c-.68 0-1.37-.26-1.89-.78-.05-.04-2.06-1.88-6.11-1.88-4.05 0-6.06 1.84-6.14 1.91-1.07 1-2.75.97-3.76-.07a2.65 2.65 0 01.01-3.73c.36-.35 3.63-3.45 9.89-3.45 6.26 0 9.53 3.1 9.89 3.45A2.66 2.66 0 0140 35.33zm-5.33-16H40v5.34h-5.33v-5.34zm-10.67 0h5.33v5.34H24v-5.34z",
                    clipRule: "evenodd"
                })), r.createElement($.hE, null, (0,
                c.JK)("BRAVE_NEWS_OFFLINE_TITLE")), r.createElement("div", null, (0,
                c.JK)("BRAVE_NEWS_OFFLINE_MESSAGE")), r.createElement(te, {
                    onClick: e
                }, (0,
                c.JK)("BRAVE_NEWS_REFRESH_FEED")))
            }
            ), null),
            [d.HLt.NoArticles]: r.createElement((function() {
                return r.createElement(ee, {
                    align: "center",
                    direction: "column",
                    justify: "center",
                    gap: l.YK.m
                }, r.createElement("svg", {
                    xmlns: "http://www.w3.org/2000/svg",
                    width: "99",
                    height: "88",
                    viewBox: "0 0 99 88",
                    fill: "none"
                }, r.createElement("path", {
                    d: "M9.5 0.5C4.80558 0.5 1 4.30558 1 9V79C1 83.6944 4.80558 87.5 9.5 87.5H89.5C94.1944 87.5 98 83.6944 98 79V9C98 4.30558 94.1944 0.5 89.5 0.5H9.5Z",
                    stroke: "url(#paint0_linear_5051_10730)"
                }), r.createElement("path", {
                    d: "M9.5 13C9.5 10.7909 11.2909 9 13.5 9H85.5C87.7091 9 89.5 10.7909 89.5 13V52C89.5 54.2091 87.7091 56 85.5 56H13.5C11.2909 56 9.5 54.2091 9.5 52V13Z",
                    fill: "url(#paint1_linear_5051_10730)"
                }), r.createElement("rect", {
                    x: "9.5",
                    y: "69",
                    width: "80",
                    height: "4",
                    rx: "2",
                    fill: "url(#paint2_linear_5051_10730)"
                }), r.createElement("rect", {
                    x: "9.5",
                    y: "59",
                    width: "48",
                    height: "2",
                    rx: "1",
                    fill: "url(#paint3_linear_5051_10730)"
                }), r.createElement("rect", {
                    x: "9.5",
                    y: "75",
                    width: "64",
                    height: "4",
                    rx: "2",
                    fill: "url(#paint4_linear_5051_10730)"
                }), r.createElement("defs", null, r.createElement("linearGradient", {
                    id: "paint0_linear_5051_10730",
                    x1: "49.5",
                    y1: "1",
                    x2: "49.5",
                    y2: "78.5",
                    gradientUnits: "userSpaceOnUse"
                }, r.createElement("stop", {
                    stopColor: "white",
                    stopOpacity: "0.15"
                }), r.createElement("stop", {
                    offset: "1",
                    stopColor: "white",
                    stopOpacity: "0"
                })), r.createElement("linearGradient", {
                    id: "paint1_linear_5051_10730",
                    x1: "9.5",
                    y1: "33",
                    x2: "89.5",
                    y2: "33",
                    gradientUnits: "userSpaceOnUse"
                }, r.createElement("stop", {
                    stopColor: "white",
                    stopOpacity: "0.03"
                }), r.createElement("stop", {
                    offset: "1",
                    stopColor: "white",
                    stopOpacity: "0.2"
                })), r.createElement("linearGradient", {
                    id: "paint2_linear_5051_10730",
                    x1: "9.5",
                    y1: "71.0426",
                    x2: "89.5",
                    y2: "71.0425",
                    gradientUnits: "userSpaceOnUse"
                }, r.createElement("stop", {
                    stopColor: "white",
                    stopOpacity: "0.03"
                }), r.createElement("stop", {
                    offset: "1",
                    stopColor: "white",
                    stopOpacity: "0.2"
                })), r.createElement("linearGradient", {
                    id: "paint3_linear_5051_10730",
                    x1: "9.5",
                    y1: "60.0213",
                    x2: "57.5",
                    y2: "60.0213",
                    gradientUnits: "userSpaceOnUse"
                }, r.createElement("stop", {
                    stopColor: "white",
                    stopOpacity: "0.03"
                }), r.createElement("stop", {
                    offset: "1",
                    stopColor: "white",
                    stopOpacity: "0.2"
                })), r.createElement("linearGradient", {
                    id: "paint4_linear_5051_10730",
                    x1: "9.5",
                    y1: "77.0426",
                    x2: "73.5",
                    y2: "77.0425",
                    gradientUnits: "userSpaceOnUse"
                }, r.createElement("stop", {
                    stopColor: "white",
                    stopOpacity: "0.03"
                }), r.createElement("stop", {
                    offset: "1",
                    stopColor: "white",
                    stopOpacity: "0.2"
                })))), r.createElement($.hE, null, (0,
                c.JK)("BRAVE_NEWS_NO_ARTICLES_TITLE")), r.createElement("div", null, (0,
                c.JK)("BRAVE_NEWS_NO_ARTICLES_MESSAGE")))
            }
            ), null),
            [d.HLt.NoFeeds]: r.createElement((function() {
                const {setCustomizePage: e} = (0,
                o.D5)();
                return r.createElement(ne, {
                    align: "center",
                    direction: "column",
                    justify: "center",
                    gap: l.YK.m
                }, r.createElement("svg", {
                    xmlns: "http://www.w3.org/2000/svg",
                    fill: "none",
                    width: "99",
                    viewBox: "0 0 64 46"
                }, r.createElement("path", {
                    fill: "#F0F2FF",
                    fillRule: "evenodd",
                    d: "M49.67 46H13.33C5.36 46 0 41.32 0 34.37c0-5.45 3.08-10.33 7.84-12.74l-.02-.84C7.82 9.69 16.92.67 28.1.67a20.3 20.3 0 0118.37 11.65c9.74.4 17.54 8.4 17.54 18.17C64 39.33 57.84 46 49.67 46zm-3.98-28.37c-.24 0-.47.02-.7.05-1.24.14-2.4-.6-2.81-1.77A14.94 14.94 0 0028.08 6a14.88 14.88 0 00-14.92 14.79c0 .68.06 1.37.18 2.11a2.67 2.67 0 01-1.8 2.96 8.95 8.95 0 00-6.2 8.5c0 5.85 6.12 6.3 8 6.3h36.33c4.47 0 9-3.5 9-10.17 0-7.1-5.83-12.86-12.98-12.86zM40 35.33c-.68 0-1.37-.26-1.89-.78-.05-.04-2.06-1.88-6.11-1.88-4.05 0-6.06 1.84-6.14 1.91-1.07 1-2.75.97-3.76-.07a2.65 2.65 0 01.01-3.73c.36-.35 3.63-3.45 9.89-3.45 6.26 0 9.53 3.1 9.89 3.45A2.66 2.66 0 0140 35.33zm-5.33-16H40v5.34h-5.33v-5.34zm-10.67 0h5.33v5.34H24v-5.34z",
                    clipRule: "evenodd"
                })), r.createElement($.hE, null, (0,
                c.JK)("BRAVE_NEWS_NO_CONTENT_HEADING")), r.createElement("div", null, (0,
                c.JK)("BRAVE_NEWS_NO_CONTENT_MESSAGE")), r.createElement(te, {
                    onClick: () => e("news")
                }, (0,
                c.JK)("BRAVE_NEWS_NO_CONTENT_ACTION_LABEL")))
            }
            ), null)
        };
        function he({feed: e, onViewCountChange: t, onSessionStart: n}) {
            var o;
            const [a,i] = r.useState(oe(ue, de));
            r.useEffect(( () => {
                re({
                    [ue]: a
                })
            }
            ), [a]),
            r.useEffect(( () => {
                const e = oe(me, void 0);
                if (e) {
                    const t = e.innerHeight === window.innerHeight && e.innerWidth === window.innerWidth ? () => {
                        var t;
                        return null === (t = document.scrollingElement) || void 0 === t ? void 0 : t.scrollTo({
                            top: e.scrollPos
                        })
                    }
                    : () => {
                        var t;
                        return null === (t = document.querySelector(`[data-id="${e.itemId}"]`)) || void 0 === t ? void 0 : t.scrollIntoView()
                    }
                    ;
                    t()
                }
            }
            ), []);
            const l = r.useRef(new IntersectionObserver((e => {
                e.some((e => {
                    var t;
                    return (null === (t = e.target) || void 0 === t ? void 0 : t.classList.contains(ie)) && 0 !== e.intersectionRatio
                }
                )) && i((e => e + de))
            }
            ),{
                rootMargin: "0px 0px 1000px 0px"
            }))
              , s = r.useRef(0)
              , c = r.useRef(null)
              , d = r.useRef(new IntersectionObserver((e => {
                const r = e.filter((e => 1 === e.intersectionRatio)).map((e => Number(e.target.getAttribute(pe))));
                if (!r.length)
                    return;
                n && (!c.current || (new Date).getTime() - ge > c.current.getTime()) && n(),
                c.current = new Date;
                const o = Math.max(...r);
                if (s.current >= o)
                    return;
                const a = o - s.current;
                s.current = o,
                t && t(a)
            }
            ),{
                threshold: 1
            }))
              , m = r.useCallback((e => {
                e && d.current.observe(e)
            }
            ), [])
              , u = r.useCallback((e => {
                l.current.disconnect(),
                e && l.current.observe(e)
            }
            ), [])
              , p = r.useMemo(( () => {
                var t;
                const n = Math.min(null !== (t = null == e ? void 0 : e.items.length) && void 0 !== t ? t : 0, a);
                let o = 0;
                const i = e => t => {
                    e === n - 1 && u(t),
                    m(t)
                }
                ;
                return null == e ? void 0 : e.items.slice(0, n).map(( (e, t) => {
                    let n;
                    if (e.advert)
                        n = r.createElement(F, {
                            info: e.advert
                        });
                    else if (e.article)
                        n = r.createElement(j, {
                            info: e.article,
                            feedDepth: o
                        });
                    else if (e.cluster)
                        n = r.createElement(L, {
                            info: e.cluster,
                            feedDepth: o
                        });
                    else if (e.discover)
                        n = r.createElement(P, {
                            info: e.discover
                        });
                    else {
                        if (!e.hero)
                            throw new Error("Invalid item!" + JSON.stringify(e));
                        n = r.createElement(G, {
                            info: e.hero,
                            feedDepth: o
                        })
                    }
                    e.cluster ? o += e.cluster.articles.length : e.advert || o++;
                    const a = se(e, t);
                    return r.createElement("div", {
                        className: ie,
                        onClickCapture: ve(a),
                        key: a,
                        "data-id": a,
                        [pe]: o,
                        ref: i(t)
                    }, n)
                }
                ))
            }
            ), [a, null == e ? void 0 : e.items, m]);
            return r.createElement(le, {
                className: ce
            }, e ? null !== (o = be[e.error]) && void 0 !== o ? o : r.createElement(r.Fragment, null, p, r.createElement(D, null)) : r.createElement(Z, null))
        }
        const fe = n.p + "a000e9296a048733701809c0863ed291.svg"
          , Ee = a.Ay.div.withConfig({
            displayName: "Container",
            componentId: "sc-1m2mx28"
        })`
  background: rgba(53, 53, 53, 0.47);
  backdrop-filter: blur(62px);
  border-radius: 16px;
  padding: 44px 82px 36px;
  width: 680px;

  color: ${l.yW.text.primary};
  font: ${l.gx.default.regular};
  text-align: center;

  display: flex;
  flex-direction: column;
  gap: 32px;

  > * {
    display: flex;
    flex-direction: column;
    gap: 16px;
  }

  h3 {
    font: ${l.gx.heading.h3};
    margin: 0;
  }

  p {
    margin: 0;
  }

  a {
    color: inherit;
  }

  .graphic {
    background-image: url(${fe});
    background-size: contain;
    background-position: center;
    background-repeat: no-repeat;
    height: 60px;
  }
`
          , we = (0,
        c.OE)("BRAVE_NEWS_INTRO_DESCRIPTION_TWO", {
            $1: e => r.createElement(s.Ay, {
                href: "https://brave.com/privacy/browser/"
            }, e)
        });
        function ye() {
            const {toggleBraveNewsOnNTP: e} = (0,
            o.D5)();
            return r.createElement(Ee, {
                "data-theme": "dark",
                className: ce
            }, r.createElement("div", {
                className: "graphic"
            }), r.createElement("h3", null, (0,
            c.JK)("BRAVE_NEWS_INTRO_TITLE")), r.createElement("div", null, r.createElement("p", null, (0,
            c.JK)("BRAVE_NEWS_INTRO_DESCRIPTION")), r.createElement("p", null, we)), r.createElement("div", null, r.createElement(i.A, {
                kind: "filled",
                onClick: () => e(!0)
            }, (0,
            c.JK)("BRAVE_NEWS_OPT_IN_ACTION_LABEL")), r.createElement(i.A, {
                kind: "plain-faint",
                onClick: () => e(!1)
            }, (0,
            c.JK)("BRAVE_NEWS_OPT_OUT_ACTION_LABEL"))))
        }
        const _e = a.Ay.div.withConfig({
            componentId: "sc-hd1ndn"
        })`
  --bn-text-base: 255, 255, 255;
  --bn-glass-container: rgba(255,255,255,0.05);
  --bn-glass-10: rgba(255, 255, 255, 0.1);
  --bn-glass-25: rgba(255, 255, 255, 0.25);
  --bn-glass-50: rgba(255, 255, 255, 0.5);
  --bn-glass-70: rgba(255, 255, 255, 0.7);
  --bn-glass-100: rgba(255, 255, 255, 1);
`;
        var xe = n("../../../brave/components/brave_news/browser/resources/SettingsButton.tsx")
          , Ce = n("../../../brave/components/common/useMediaQuery.ts");
        const Ae = r.lazy(( () => n.e("brave_components_brave_news_browser_resources_SidebarMenu_tsx").then(n.bind(n, "../../../brave/components/brave_news/browser/resources/SidebarMenu.tsx"))))
          , Ne = r.lazy(( () => n.e("brave_components_brave_news_browser_resources_FeedNavigation_tsx").then(n.bind(n, "../../../brave/components/brave_news/browser/resources/FeedNavigation.tsx"))))
          , Ie = "(max-width: 1024px)"
          , ke = (0,
        a.Ay)(_e).withConfig({
            displayName: "Root",
            componentId: "sc-1lv52yb"
        })`
  --bn-top-bar-height: 78px;

  padding-top: ${l.YK.xl};

  display: grid;
  grid-template-columns: 1fr max-content 1fr;
  gap: ${l.YK["3Xl"]};
`
          , $e = a.Ay.div.withConfig({
            displayName: "SidebarContainer",
            componentId: "sc-1r66mqy"
        })`
  position: sticky;
  top: ${l.YK.xl};
`
          , Se = a.Ay.div.withConfig({
            displayName: "ButtonsContainer",
            componentId: "sc-thg72u"
        })`
  position: fixed;
  bottom: ${l.YK["5Xl"]};
  right: ${l.YK["5Xl"]};
  border-radius: ${l.r8.m};
  padding: ${l.YK.m};

  background: var(--bn-glass-container);
  backdrop-filter: blur(64px);

  @media ${Ie} {
    height: var(--bn-top-bar-height);

    inset: 0;
    bottom: unset;
    padding: ${l.YK["2Xl"]} ${l.YK.xl};
    border-radius: 0;
  }
`
          , Te = a.Ay.div.withConfig({
            displayName: "ButtonSpacer",
            componentId: "sc-10egqc7"
        })`
  max-width: min(540px, 100vw);

  display: flex;
  justify-content: flex-end;
  gap: ${l.YK.m};

  margin-left: auto;
  margin-right: auto;
`
          , Re = (0,
        a.Ay)(te).withConfig({
            displayName: "LoadNewContentButton",
            componentId: "sc-1bkgfkj"
        })`
  position: fixed;
  z-index: 1;
  top: ${l.YK["3Xl"]};

  flex-grow: 0;

  @media ${Ie} {
    top: calc(var(--bn-top-bar-height) + var(--leo-spacing-m));
  }
`;
        function Ke() {
            const e = (0,
            Ce.A)(Ie)
              , {feedV2: t, setCustomizePage: n, refreshFeedV2: a, feedV2UpdatesAvailable: i, reportViewCount: s, reportSessionStart: d} = (0,
            o.D5)()
              , m = r.useRef();
            return r.useLayoutEffect(( () => {
                m.current && m.current.getBoundingClientRect().top < window.innerHeight / 2 && m.current.scrollIntoView()
            }
            ), [null == t ? void 0 : t.items]),
            r.createElement(ke, {
                ref: m,
                "data-theme": "dark"
            }, r.createElement($e, {
                className: "brave-news-sidebar"
            }, !e && r.createElement(r.Suspense, {
                fallback: null
            }, r.createElement(Ne, null))), r.createElement(g.A, {
                align: "center",
                direction: "column",
                gap: l.YK.l
            }, i && r.createElement(Re, {
                className: "brave-news-load-new-content-button",
                onClick: a
            }, (0,
            c.JK)("BRAVE_NEWS_NEW_CONTENT_AVAILABLE")), r.createElement(he, {
                feed: t,
                onViewCountChange: s,
                onSessionStart: d
            })), r.createElement(Se, {
                className: "brave-news-feed-controls"
            }, r.createElement(Te, null, e && r.createElement(r.Suspense, {
                fallback: null
            }, r.createElement(Ae, null)), r.createElement(xe.A, {
                onClick: () => n("news"),
                title: (0,
                c.JK)("BRAVE_NEWS_CUSTOMIZE_FEED")
            }, r.createElement(b.Ay, {
                name: "tune"
            })), r.createElement(xe.A, {
                isLoading: !t,
                title: (0,
                c.JK)("BRAVE_NEWS_REFRESH_FEED"),
                onClick: () => {
                    a()
                }
            }, r.createElement(b.Ay, {
                name: "refresh"
            })))))
        }
        const Oe = r.lazy(( () => n.e("brave_components_brave_news_browser_resources_customize_Configure_tsx").then(n.bind(n, "../../../brave/components/brave_news/browser/resources/customize/Configure.tsx"))))
          , Be = a.Ay.dialog.withConfig({
            displayName: "Dialog",
            componentId: "sc-ak8vts"
        })`
  font: ${l.gx.default.regular};
  border-radius: 8px;
  border: none;
  margin: auto;
  width: min(100vw, 1049px);
  height: min(100vh, 712px);
  z-index: 1000;
  background: white;
  overflow: hidden;
  padding: 0;
  background-color: ${l.yW.container.background};
  color:  ${l.yW.text.primary};
`
          , Fe = a.Ay.div.withConfig({
            displayName: "Loading",
            componentId: "sc-bztqr6"
        })`
  --leo-progressring-size: 50px;

  display: flex;
  align-items: center;
  justify-content: center;
  height: 100%;
`;
        function ze() {
            const {customizePage: e, setCustomizePage: t} = (0,
            o.D5)()
              , n = r.useRef()
              , a = !!e;
            return r.useEffect(( () => {
                var e, r, o, i, l, s, c;
                a && !(null === (e = n.current) || void 0 === e ? void 0 : e.open) ? null === (o = null === (r = n.current) || void 0 === r ? void 0 : r.showModal) || void 0 === o || o.call(r) : !a && (null === (i = n.current) || void 0 === i ? void 0 : i.open) && (null === (s = null === (l = n.current) || void 0 === l ? void 0 : l.close) || void 0 === s || s.call(l));
                const d = () => t(null);
                return null === (c = n.current) || void 0 === c || c.addEventListener("cancel", d),
                () => {
                    var e;
                    null === (e = n.current) || void 0 === e || e.removeEventListener("cancel", d)
                }
            }
            ), [a, n]),
            a ? r.createElement(Be, {
                ref: n
            }, r.createElement(r.Suspense, {
                fallback: r.createElement(Fe, null, r.createElement(q.A, null))
            }, r.createElement(Oe, null))) : null
        }
        var je = n("../../../brave/browser/resources/brave_new_tab_page_refresh/context/new_tab_context.ts");
        const Ve = n("../../../brave/browser/resources/brave_new_tab_page_refresh/lib/scoped_css.ts").P.css`
  & {
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    align-items: center;
    margin: 0 30px 30px;
  }
`;
        function De() {
            const e = (0,
            o.D5)()
              , t = (0,
            je.QY)((e => e.newsFeatureEnabled))
              , [n,a] = r.useState(!1);
            return r.useEffect(( () => {
                setTimeout(( () => a(!0)), 1e3)
            }
            ), []),
            t ? r.createElement(r.Fragment, null, e.isShowOnNTPPrefEnabled && r.createElement("div", {
                "data-css-scope": Ve.scope
            }, e.isOptInPrefEnabled ? n && r.createElement(Ke, null) : r.createElement(ye, null)), e.customizePage && r.createElement(ze, null)) : null
        }
        Ve.passthrough.css`
  @keyframes news-control-fade {
    from {
      opacity: 0;
      visibility: hidden;
    }
    80% {
      opacity: 0;
      visibility: visible;
    }
    to {
      opacity: 1;
      visibility: visible;
    }
  }

  .brave-news-feed-controls, .brave-news-load-new-content-button {
    animation: linear news-control-fade both;
    animation-timeline: scroll();
    animation-range: 0px 100vh;
  }
`;
        const Ye = De
    }
    ,
    "../../../brave/components/brave_news/browser/resources/SettingsButton.tsx": (e, t, n) => {
        n.d(t, {
            A: () => i
        });
        var r = n("../../../brave/node_modules/@brave/leo/react/button.js")
          , o = n("../../../brave/node_modules/@brave/leo/tokens/css/variables.js");
        const a = (0,
        n("../../../brave/node_modules/styled-components/dist/styled-components.esm.js").Ay)(r.A).withConfig({
            displayName: "SettingsButton",
            componentId: "sc-1nr7avu"
        })`
  --leo-button-color: var(--bn-glass-50);
  --leo-button-radius: ${o.r8.s};
  --leo-button-padding: ${o.YK.s};

  flex: 0;
`;
        a.defaultProps = {
            fab: !0,
            kind: "outline"
        };
        const i = a
    }
    ,
    "../../../brave/components/brave_news/browser/resources/feed/Card.tsx": (e, t, n) => {
        n.d(t, {
            Ay: () => p,
            Ql: () => g,
            Sx: () => v,
            hE: () => s,
            v1: () => u,
            v5: () => m
        });
        var r = n("../../../brave/node_modules/react/index.js")
          , o = n("../../../brave/node_modules/@brave/leo/tokens/css/variables.js")
          , a = n("../../../brave/node_modules/styled-components/dist/styled-components.esm.js")
          , i = n("../../../brave/components/common/SecureLink.tsx")
          , l = n("../../../brave/components/brave_news/browser/resources/shared/Context.tsx");
        a.Ay.h2.withConfig({
            displayName: "Header",
            componentId: "sc-1giqpcn"
        })`
  margin: 0;

  font: ${o.gx.heading.h2};
  color: var(--bn-glass-100);

  --leo-icon-size: 18px;
`;
        const s = a.Ay.h3.withConfig({
            displayName: "Title",
            componentId: "sc-s9l73p"
        })`
  --leo-icon-color: ${o.yW.icon.default};

  display: flex;
  align-items: center;

  margin: 0;

  text-align: start;
  font: ${o.gx.default.semibold};
  color: var(--bn-glass-100);


  &> a { all: unset; }
`
          , c = a.Ay.img.withConfig({
            displayName: "BaseImg",
            componentId: "sc-w1fzbb"
        })`
  opacity: 0;
  transition: opacity 400ms ease-in-out;
`
          , d = ({onError: e, onLoad: t, targetHeight: n, targetWidth: o, src: a, loading: i, ...s}) => {
            const d = r.useRef()
              , {shouldRenderImages: m} = (0,
            l.D5)()
              , u = !m && "lazy" === i
              , p = r.useCallback((e => {
                d.current.style.opacity = "1",
                null == t || t(e)
            }
            ), [t]);
            return a && (a = "chrome://brave-image?url=" + encodeURIComponent(a)),
            n && o && (a += `&target_size=${Math.round(o * window.devicePixelRatio)}x${Math.round(n * window.devicePixelRatio)}`),
            r.createElement(c, {
                ...s,
                src: u ? void 0 : a,
                loading: i,
                ref: d,
                onLoad: p
            })
        }
          , m = (0,
        a.Ay)(d).attrs({
            targetHeight: 64,
            targetWidth: 96
        }).withConfig({
            displayName: "SmallImage",
            componentId: "sc-vr7ap8"
        })`
  &:not([src]) { opacity: 0; }

  min-width: 96px;
  width: 96px;

  height: 64px;

  object-fit: cover;
  object-position: top;

  border-radius: 6px;
`
          , u = (0,
        a.Ay)(d).attrs({
            targetHeight: 269,
            targetWidth: 508
        }).withConfig({
            displayName: "LargeImage",
            componentId: "sc-w6wtfh"
        })`
  &:not([src]) { opacity: 0; }

  width: 100%;
  height: 269px;

  object-fit: cover;
  object-position: top;

  border-radius: 6px;
`
          , p = a.Ay.div.withConfig({
            componentId: "sc-1r174zo"
        })`
  text-decoration: none;
  background: var(--bn-glass-container);
  border-radius: ${o.r8.xl};
  color: var(--bn-glass-100);
  padding: ${o.YK.xl};

  &:has(${s} a:focus-visible) {
    box-shadow: ${o.QZ.focusState};
  }

  ${e => e.onClick && "cursor: pointer"}
`
          , g = (e, t=i.Sz) => n => {
            (0,
            i.wF)(e, t),
            l.$z.value.openArticlesInNewTab || n.ctrlKey || n.metaKey || 4 & n.buttons ? window.open(e, "_blank", "noopener noreferrer") : window.location.href = e
        }
        ;
        function v({feedDepth: e, ...t}) {
            const n = {
                feeddepth: e,
                ...t
            }
              , {openArticlesInNewTab: o, reportVisit: a} = (0,
            l.D5)();
            return r.createElement(i.Ay, {
                ...n,
                onClick: t => {
                    t.stopPropagation(),
                    void 0 !== e && a(e)
                }
                ,
                target: o ? "_blank" : void 0
            })
        }
    }
    ,
    "../../../brave/components/brave_news/browser/resources/shared/FollowButton.tsx": (e, t, n) => {
        n.d(t, {
            A: () => l
        });
        var r = n("../../../brave/node_modules/@brave/leo/react/button.js")
          , o = n("../../../brave/node_modules/@brave/leo/react/icon.js")
          , a = n("../../../brave/node_modules/react/index.js");
        const i = (0,
        n("../../../brave/node_modules/styled-components/dist/styled-components.esm.js").Ay)(r.A).withConfig({
            displayName: "StyledButton",
            componentId: "sc-1ts7m29"
        })`
  --leo-button-color: rgba(150, 150, 150, 0.8);
  backdrop-filter: blur(64px);
`;
        function l(e) {
            const {following: t, ...n} = e;
            return a.createElement(i, {
                ...n,
                fab: !0,
                size: "tiny"
            }, a.createElement(o.Ay, {
                name: t ? "minus" : "plus-add"
            }))
        }
    }
    ,
    "../../../brave/components/brave_news/browser/resources/shared/PublisherCard.tsx": (e, t, n) => {
        n.d(t, {
            q: () => b,
            A: () => v
        });
        var r = n("../../../brave/components/common/Flex.tsx")
          , o = n("../../../brave/node_modules/react/index.js")
          , a = n("../../../brave/node_modules/styled-components/dist/styled-components.esm.js");
        const i = ["#FF9AA2", "#FFB7B2", "#FFDAC1", "#E2F0CB", "#B5EAD7", "#C7CEEA"]
          , l = e => {
            const t = "string" == typeof e ? (e => {
                let t = 0;
                for (let n = 0; n < e.length; ++n)
                    t = Math.imul(31, t) + e.charCodeAt(n);
                return 2147483647 + (0 | t) + 1
            }
            )(e) : e;
            return i[t % i.length]
        }
        ;
        var s = n("../../../brave/components/brave_news/browser/resources/shared/Context.tsx")
          , c = n("../../../brave/components/brave_news/browser/resources/shared/FollowButton.tsx")
          , d = n("../../../brave/components/brave_news/browser/resources/shared/api.ts");
        const m = (0,
        a.Ay)(c.A).withConfig({
            displayName: "StyledFollowButton",
            componentId: "sc-nlaef0"
        })`
  position: absolute;
  right: 8px;
  top: 8px;
`
          , u = (0,
        a.Ay)("div").attrs((e => ({
            style: {
                backgroundColor: e.backgroundColor
            }
        }))).withConfig({
            displayName: "Card",
            componentId: "sc-rjkokg"
        })`
  position: relative;
  height: 80px;
  border-radius: 8px;
  overflow: hidden;
  box-shadow: 0px 0px 16px 0px #63696E2E;

  &[data-feed-card-is-followed=true] {
    &:not(:hover, :has(:focus-visible)) ${m} {
      opacity: 0;
    }
  }
`
          , p = (0,
        a.Ay)("div").attrs((e => ({
            style: {
                backgroundImage: `url('${e.backgroundImage}')`
            }
        }))).withConfig({
            displayName: "CoverImage",
            componentId: "sc-1ahmej8"
        })`
  position: absolute;
  top: 15%; bottom: 15%; left: 15%; right: 15%;
  border-radius: 8px;
  background-position: center;
  background-size: contain;
  background-repeat: no-repeat;
`
          , g = a.Ay.span.withConfig({
            displayName: "Name",
            componentId: "sc-152s049"
        })`
  font-size: 14px;
  font-weight: 600;
`;
        function v(e) {
            var t, n;
            const a = (0,
            s.qM)(e.publisherId)
              , {followed: i, setFollowed: c} = (0,
            s.oZ)(e.publisherId)
              , d = (null == a ? void 0 : a.backgroundColor) || l((null === (t = null == a ? void 0 : a.feedSource) || void 0 === t ? void 0 : t.url) || (null == a ? void 0 : a.publisherId))
              , v = null === (n = null == a ? void 0 : a.coverUrl) || void 0 === n ? void 0 : n.url;
            return o.createElement(r.A, {
                direction: "column",
                gap: 8
            }, o.createElement(u, {
                backgroundColor: d,
                "data-feed-card-is-followed": i
            }, v && o.createElement(p, {
                backgroundImage: `chrome://brave-image?url=${encodeURIComponent(v)}`
            }), o.createElement(m, {
                fab: !0,
                size: "tiny",
                following: i,
                onClick: () => c(!i)
            })), o.createElement(g, null, null == a ? void 0 : a.publisherName))
        }
        function b(e) {
            const [t,n] = (0,
            o.useState)(!1);
            return o.createElement(r.A, {
                direction: "column",
                gap: 8
            }, o.createElement(u, {
                backgroundColor: l(e.feedUrl),
                "data-feed-card-is-followed": !0
            }, o.createElement(m, {
                following: !1,
                isDisabled: t,
                onClick: async () => {
                    n(!0),
                    await (0,
                    d.Ay$)().subscribeToNewDirectFeed({
                        url: e.feedUrl
                    }),
                    n(!1)
                }
            })), o.createElement(g, null, e.title))
        }
    }
    ,
    "../../../brave/components/common/Flex.tsx": (e, t, n) => {
        n.d(t, {
            A: () => r
        });
        const r = (0,
        n("../../../brave/node_modules/styled-components/dist/styled-components.esm.js").Ay)("div").withConfig({
            displayName: "Flex",
            componentId: "sc-ycfuep"
        })`
  display: flex;
  flex-direction: ${e => e.direction};
  justify-content: ${e => e.justify};
  align-items: ${e => e.align};
  gap: ${e => "number" == typeof e.gap ? `${e.gap}px` : e.gap};
  flex-wrap: ${e => e.wrap};
`
    }
    ,
    "../../../brave/components/common/SecureLink.tsx": (e, t, n) => {
        n.d(t, {
            Ay: () => i,
            Sz: () => o,
            wF: () => a
        });
        var r = n("../../../brave/node_modules/react/index.js");
        const o = ["http:", "https:"]
          , a = (e, t=o) => {
            if (!e)
                return;
            const n = new URL(e);
            if (!t.includes(n.protocol))
                throw new Error(`Unsupported scheme ${n.protocol} on url ${e}`)
        }
        ;
        function i({href: e, allowedSchemes: t, ...n}) {
            return a(e, null != t ? t : o),
            r.createElement("a", {
                href: e,
                ...n
            })
        }
    }
};
