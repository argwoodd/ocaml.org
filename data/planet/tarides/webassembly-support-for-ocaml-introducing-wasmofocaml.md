---
title: 'WebAssembly Support for OCaml: Introducing Wasm_of_Ocaml'
description: "OCaml is constantly evolving. Developers collaborate to bring support
  for new features, improve workflows, and resolve pain points. To this\u2026"
url: https://tarides.com/blog/2023-11-01-webassembly-support-for-ocaml-introducing-wasm-of-ocaml
date: 2023-11-01T00:00:00-00:00
preview_image: https://tarides.com/static/e237be0dac96cc75a61584cee7c7d1f5/b2176/prisms.jpg
featured:
authors:
- Tarides
source:
---

<p>OCaml is constantly evolving. Developers collaborate to bring support for new features, improve workflows, and resolve pain points. To this end, the <a href="https://github.com/ocaml-wasm">OCaml-Wasm</a> GitHub organisation was recently established. Its goal is to bring WebAssembly support to OCaml.</p>
<p>WebAssembly, more commonly known as Wasm, is a low-level virtual machine that is both language- and platform-independent. In essence, Wasm is a binary format designed as a portable compilation target for programming languages. It enables deployment on a variety of platforms like web browsers, cloud, blockchain, and mobile.</p>
<p>Wasm makes no assumptions about language features or operations. As a result, Wasm is technically compatible with any programming language since its code can be interpreted as virtual hardware.</p>
<h2 style="position:relative;"><a href="https://tarides.com/feed.xml#why-webassembly" aria-label="why webassembly permalink" class="anchor before"><svg aria-hidden="true" focusable="false" height="16" version="1.1" viewbox="0 0 16 16" width="16"><path fill-rule="evenodd" d="M4 9h1v1H4c-1.5 0-3-1.69-3-3.5S2.55 3 4 3h4c1.45 0 3 1.69 3 3.5 0 1.41-.91 2.72-2 3.25V8.59c.58-.45 1-1.27 1-2.09C10 5.22 8.98 4 8 4H4c-.98 0-2 1.22-2 2.5S3 9 4 9zm9-3h-1v1h1c1 0 2 1.22 2 2.5S13.98 12 13 12H9c-.98 0-2-1.22-2-2.5 0-.83.42-1.64 1-2.09V6.25c-1.09.53-2 1.84-2 3.25C6 11.31 7.55 13 9 13h4c1.45 0 3-1.69 3-3.5S14.5 6 13 6z"></path></svg></a>Why WebAssembly</h2>
<p>You might be wondering why you should care about Wasm support in OCaml. Well, Wasm has several advantages that make it popular with developers and organisations all over the world. Briefly, they are:</p>
<ul>
<li><strong>Security:</strong> Wasm has a fully formalised type system and semantics. Wasm engines validate (type check) code and execute it in a memory-safe, isolated environment known as a sandbox. Wasm code performs predictably, with no crashes or unexpected actions, and within restrictions that limit access to the user's local resources.</li>
<li><strong>Speed:</strong> Wasm can take advantage of language implementation techniques like just-in-time (JIT) and ahead-of-time (AOT) compilation, alongside other capabilities common to contemporary hardware. It allows Wasm code to perform at near-native code levels of performance.</li>
<li><strong>Openness:</strong> Wasm is an open standard, meaning that it and all its documentation are openly and freely accessible to developers. Anyone can influence the evolution of Wasm by participating in the <a href="https://www.w3.org/community/webassembly/">W3C Community Group</a>.</li>
<li><strong>Language Neutrality:</strong> As previously mentioned Wasm works by abstracting hardware and doesn't make any assumptions about language features. It makes Wasm language-neutral, meaning it does not privilege any language, programming, or object model above another.</li>
<li><strong>Platform Independence:</strong> Wasm can be built and deployed on different platforms regardless of the OS, hardware, or programming language as long as the Wasm virtual machine is supported.</li>
<li><strong>Browser Support:</strong> Wasm is supported by all major browsers including Chrome, Mozilla Firefox, and Safari.</li>
</ul>
<h3 style="position:relative;"><a href="https://tarides.com/feed.xml#who-is-using-wasm" aria-label="who is using wasm permalink" class="anchor before"><svg aria-hidden="true" focusable="false" height="16" version="1.1" viewbox="0 0 16 16" width="16"><path fill-rule="evenodd" d="M4 9h1v1H4c-1.5 0-3-1.69-3-3.5S2.55 3 4 3h4c1.45 0 3 1.69 3 3.5 0 1.41-.91 2.72-2 3.25V8.59c.58-.45 1-1.27 1-2.09C10 5.22 8.98 4 8 4H4c-.98 0-2 1.22-2 2.5S3 9 4 9zm9-3h-1v1h1c1 0 2 1.22 2 2.5S13.98 12 13 12H9c-.98 0-2-1.22-2-2.5 0-.83.42-1.64 1-2.09V6.25c-1.09.53-2 1.84-2 3.25C6 11.31 7.55 13 9 13h4c1.45 0 3-1.69 3-3.5S14.5 6 13 6z"></path></svg></a>Who is Using Wasm?</h3>
<p>Currently, several companies and organisations use Wasm. For example, the cross-platform game engine  <a href="https://unity.com">Unity</a> is <a href="https://blog.unity.com/technology/webassembly-is-here">using Wasm</a> to reduce code size, manage memory, and improve load times.  <a href="https://docs.fastly.com">Fastly</a> also uses Wasm. Fastly is a company that offers numerous Network Services for their <a href="https://docs.fastly.com/products/compute-at-edge">Compute@Edge</a> platform. <a href="https://www.figma.com">Figma</a>, an online collaborative design platform, also uses Wasm to <a href="https://www.figma.com/blog/webassembly-cut-figmas-load-time-by-3x/">cut their loading times</a>. These are just a few examples of how Wasm is being used to great effect, illustrating the potential and desirability of Wasm.</p>
<h3 style="position:relative;"><a href="https://tarides.com/feed.xml#future-features" aria-label="future features permalink" class="anchor before"><svg aria-hidden="true" focusable="false" height="16" version="1.1" viewbox="0 0 16 16" width="16"><path fill-rule="evenodd" d="M4 9h1v1H4c-1.5 0-3-1.69-3-3.5S2.55 3 4 3h4c1.45 0 3 1.69 3 3.5 0 1.41-.91 2.72-2 3.25V8.59c.58-.45 1-1.27 1-2.09C10 5.22 8.98 4 8 4H4c-.98 0-2 1.22-2 2.5S3 9 4 9zm9-3h-1v1h1c1 0 2 1.22 2 2.5S13.98 12 13 12H9c-.98 0-2-1.22-2-2.5 0-.83.42-1.64 1-2.09V6.25c-1.09.53-2 1.84-2 3.25C6 11.31 7.55 13 9 13h4c1.45 0 3-1.69 3-3.5S14.5 6 13 6z"></path></svg></a>Future Features</h3>
<p>The current <a href="https://webassembly.github.io/spec/core/">Wasm core specification</a>, whilst very useful for performance-critical tasks deployed on the cloud, is still quite simplistic. Users need to go through JavaScript to manipulate the DOM and also need to explicitly keep track of pointers to JavaScript values. Consequently, it is currently not feasible to write large web applications in Wasm.</p>
<p>That is all about to change as there are multiple proposals to bring new features to Wasm. The most relevant to OCaml is the <a href="https://github.com/WebAssembly/gc/blob/main/proposals/gc/MVP.md">Garbage Collection proposal</a> which will provide heap-allocated data structures that are garbage collected and can directly contain references to foreign values. It is being implemented together with the <a href="https://github.com/WebAssembly/function-references">typed function references</a> proposal. They are expected to ship in November on both Chrome and Firefox. Another proposal includes support for <a href="https://github.com/WebAssembly/tail-call">tail calls</a>. These forward-looking features will make Wasm applicable for an even wider range of uses.</p>
<h2 style="position:relative;"><a href="https://tarides.com/feed.xml#webassembly-and-ocaml" aria-label="webassembly and ocaml permalink" class="anchor before"><svg aria-hidden="true" focusable="false" height="16" version="1.1" viewbox="0 0 16 16" width="16"><path fill-rule="evenodd" d="M4 9h1v1H4c-1.5 0-3-1.69-3-3.5S2.55 3 4 3h4c1.45 0 3 1.69 3 3.5 0 1.41-.91 2.72-2 3.25V8.59c.58-.45 1-1.27 1-2.09C10 5.22 8.98 4 8 4H4c-.98 0-2 1.22-2 2.5S3 9 4 9zm9-3h-1v1h1c1 0 2 1.22 2 2.5S13.98 12 13 12H9c-.98 0-2-1.22-2-2.5 0-.83.42-1.64 1-2.09V6.25c-1.09.53-2 1.84-2 3.25C6 11.31 7.55 13 9 13h4c1.45 0 3-1.69 3-3.5S14.5 6 13 6z"></path></svg></a>WebAssembly and OCaml</h2>
<p>With all these benefits and future potential, it's not hard to see why the community is eager to see support for Wasm in OCaml. Using Wasm as a compilation target will allow for faster web performance (in comparison to JavaScript) as well as potentially unlocking new platforms on which to run OCaml.  The <a href="https://github.com/ocaml-wasm">OCaml-Wasm</a> organisation is bringing previous efforts together to collaborate on implementing WebAssembly for OCaml.</p>
<p>There are two main prongs of the effort at the moment. One is <code>wasocaml</code>, an <a href="https://ocamlpro.com/blog/2022_12_14_wasm_and_ocaml/">experimental compiler backend</a> that targets Wasm using the Flambda intermediate representation of the OCaml compiler.  Engineers at <a href="https://ocamlpro.com">OCamlPro</a> are behind this approach and you can <a href="https://github.com/ocaml-wasm/wasocaml">check out the repo here</a>.</p>
<p>The other approach uses a toolchain to compile OCaml to Wasm based on the tried-and-tested <a href="https://github.com/ocsigen/js_of_ocaml"><code>js_of_ocaml</code></a> method. Called <a href="https://github.com/ocaml-wasm/wasm_of_ocaml"><code>wasm_of_ocaml</code></a>, this toolchain takes OCaml bytecode as input and emits Wasm.</p>
<p>It is relevant to mention two other methods created to run OCaml programs using Wasm runtimes. These methods are appropriate for use cases where the speed of generated code is less of a concern, and differ from <code>wasocaml</code> and <code>wasm_of_ocaml</code> by being mainly intended for server-side applications. Both <a href="https://github.com/sebmarkbage/ocamlrun-wasm"><code>ocamlrun-wasm</code></a> and <a href="https://github.com/remixlabs/wasicaml"><code>wasicaml</code></a> are ports of the OCaml bytecode interpreter to Wasm. Wasicaml also has a compiler mode that parses bytecode executable and translates it to Wasm in a similar way to <code>wasm_of_ocaml</code>, but simpler.</p>
<p>Since <code>wasm_of_ocaml</code> was and continues to be developed mainly by Tarides engineers, this article will focus on this tool. To get more information about <code>wasocaml</code>, visit <a href="https://ocamlpro.com/blog/">OCamlPro's blog</a>.</p>
<h2 style="position:relative;"><a href="https://tarides.com/feed.xml#wasm_of_ocaml" aria-label="wasm_of_ocaml permalink" class="anchor before"><svg aria-hidden="true" focusable="false" height="16" version="1.1" viewbox="0 0 16 16" width="16"><path fill-rule="evenodd" d="M4 9h1v1H4c-1.5 0-3-1.69-3-3.5S2.55 3 4 3h4c1.45 0 3 1.69 3 3.5 0 1.41-.91 2.72-2 3.25V8.59c.58-.45 1-1.27 1-2.09C10 5.22 8.98 4 8 4H4c-.98 0-2 1.22-2 2.5S3 9 4 9zm9-3h-1v1h1c1 0 2 1.22 2 2.5S13.98 12 13 12H9c-.98 0-2-1.22-2-2.5 0-.83.42-1.64 1-2.09V6.25c-1.09.53-2 1.84-2 3.25C6 11.31 7.55 13 9 13h4c1.45 0 3-1.69 3-3.5S14.5 6 13 6z"></path></svg></a>Wasm_of_OCaml</h2>
<p>As previously mentioned, <code>wasm_of_ocaml</code> is designed to use OCaml bytecode as its input to emit Wasm code. It uses the same approach as the popular  <code>js_of_ocaml</code>, which in turn compiles OCaml bytecode to JavaScript. <code>wasm_of_ocaml</code> also aims to make it possible to compile programs made for <code>js_of_ocaml</code> in <code>wasm_of_ocaml</code> with minimal changes. Both <code>js_of_ocaml</code> and <code>wasm_of_ocaml</code> are the brainchildren of J&eacute;r&ocirc;me Vouillon, currently a principal software engineer at Tarides.</p>
<p>Recently, there have been significant strides towards implementing runtime bindings in <code>wasm_of_ocaml</code>. The toolchain can now compile <code>ocamlc</code> into Wasm and run the <a href="https://github.com/janestreet/bonsai">Bonsai tests and examples</a>. The first benchmarks are encouraging, with compiled programs typically running an average of 30% faster than their <code>js_of_ocaml</code> equivalents.</p>
<p>With a large part of the <a href="https://github.com/ocaml-wasm/wasm_of_ocaml/issues/5">OCaml runtime already implemented</a>, there are several additional PRs in the works to get Wasm supported in <a href="https://github.com/ocaml/dune/pull/8278"><code>dune</code></a>, <a href="https://github.com/LexiFi/gen_js_api/pull/173"><code>gen_js_api</code></a>, and <a href="https://github.com/dbuenzli/brr/pull/51"><code>Brr</code></a>. On the whole, <code>wasm_of_ocaml</code> is getting impressively close to completion thanks to the sustained efforts of J&eacute;r&ocirc;me.</p>
<p>The process is not entirely without challenges, and some adaptations have had to be made for OCaml and Wasm to be compatible. For example, although <code>wasm_of_ocaml</code> builds on the <code>Js_of_ocaml</code> compiler to target Wasm, it still needed some extra adjustments regarding closures. JavaScript supports closures whereas Wasm doesn't, so <code>wasm_of_ocaml</code> adds a closure conversion phase to eliminate closures and instead target Wasm's closed functions.</p>
<p>There is also the need to consider support for effects, a feature new to OCaml since the <a href="https://tarides.com/blog/2022-12-19-ocaml-5-with-multicore-support-is-here/">OCaml 5 release</a>. Algebraic effects, which permit non-local control flow in a program and are useful for implementing concurrency, are supported in <code>js_of_ocaml</code> through a static analysis guided <a href="https://github.com/ocsigen/js_of_ocaml/pull/1384">selective Continuation-Passing Style (CPS)</a> transformation. <code>Wasm_of_ocaml</code> supports effect handlers in two ways, one of which is via a CPS transformation like in <code>js_of_ocaml</code>. A CPS transformation introduces overhead however, and the feature is opt-in only. The second way is through the <a href="https://v8.dev/blog/jspi">Javascript Promise Integration proposal</a>, which introduces less overhead than the CPS transformation at the cost of running another extension. Interestingly, a <a href="https://2023.splashcon.org/details/splash-2023-oopsla/48/Continuing-WebAssembly-with-Effect-Handlers">paper proposing support for effect handlers in Wasm</a> and a <a href="https://github.com/WebAssembly/stack-switching">stack switching proposal</a> present other paths to addressing effect handlers in Wasm.</p>
<h2 style="position:relative;"><a href="https://tarides.com/feed.xml#next-steps--feedback" aria-label="next steps  feedback permalink" class="anchor before"><svg aria-hidden="true" focusable="false" height="16" version="1.1" viewbox="0 0 16 16" width="16"><path fill-rule="evenodd" d="M4 9h1v1H4c-1.5 0-3-1.69-3-3.5S2.55 3 4 3h4c1.45 0 3 1.69 3 3.5 0 1.41-.91 2.72-2 3.25V8.59c.58-.45 1-1.27 1-2.09C10 5.22 8.98 4 8 4H4c-.98 0-2 1.22-2 2.5S3 9 4 9zm9-3h-1v1h1c1 0 2 1.22 2 2.5S13.98 12 13 12H9c-.98 0-2-1.22-2-2.5 0-.83.42-1.64 1-2.09V6.25c-1.09.53-2 1.84-2 3.25C6 11.31 7.55 13 9 13h4c1.45 0 3-1.69 3-3.5S14.5 6 13 6z"></path></svg></a>Next Steps &amp; Feedback</h2>
<p>It is incredibly helpful for the team to get feedback from people who try <code>wasm_of_ocaml</code>. You can contribute to the effort on <a href="https://github.com/ocaml-wasm/wasm_of_ocaml">the repo</a>, which also has instructions for how to install and use the toolchain.</p>
<p>Don't hesitate to <a href="https://tarides.com/contact/">contact us</a> if you have any questions or comments. The <a href="https://discuss.ocaml.org">Discuss Forum</a> is another great place to ask questions or share your thoughts. We look forward to seeing you around the OCaml community!</p>