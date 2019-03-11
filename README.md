// ==UserScript==
// @name        GitHub Copy Code Snippet
// @version     0.3.5
// @description A userscript adds a copy to clipboard button on hover of markdown code snippets
// @license     MIT
// @author      Rob Garrison
// @namespace   https://github.com/Mottie
// @include     https://github.com/*
// @include     https://gist.github.com/*
// @run-at      document-idle
// @grant       GM_addStyle
// @require     https://greasyfork.org/scripts/28721-mutations/code/mutations.js?version=666427
// @icon        https://github.githubassets.com/pinned-octocat.svg
// @updateURL   https://raw.githubusercontent.com/Mottie/GitHub-userscripts/master/github-copy-code-snippet.user.js
// @downloadURL https://raw.githubusercontent.com/Mottie/GitHub-userscripts/master/github-copy-code-snippet.user.js
// ==/UserScript==
(() => {
	"use strict";

	let copyId = 0;
	const markdownSelector = ".markdown-body, .markdown-format",
		codeSelector = "pre:not(.gh-csc-pre)",

		copyButton = document.createElement("clipboard-copy");
	copyButton.className = "btn btn-sm btn-blue tooltipped tooltipped-w gh-csc-button";
	copyButton.setAttribute("aria-label", "Copy to clipboard");
	// This hint isn't working yet (GitHub needs to fix it)
	copyButton.setAttribute("data-copied-hint", "Copied!");
	copyButton.innerHTML = `
		<svg aria-hidden="true" class="octicon octicon-clippy" height="16" viewBox="0 0 14 16" width="14">
			<path fill-rule="evenodd" d="M2 13h4v1H2v-1zm5-6H2v1h5V7zm2 3V8l-3 3 3 3v-2h5v-2H9zM4.5 9H2v1h2.5V9zM2 12h2.5v-1H2v1zm9 1h1v2c-.02.28-.11.52-.3.7-.19.18-.42.28-.7.3H1c-.55 0-1-.45-1-1V4c0-.55.45-1 1-1h3c0-1.11.89-2 2-2 1.11 0 2 .89 2 2h3c.55 0 1 .45 1 1v5h-1V6H1v9h10v-2zM2 5h8c0-.55-.45-1-1-1H8c-.55 0-1-.45-1-1s-.45-1-1-1-1 .45-1 1-.45 1-1 1H3c-.55 0-1 .45-1 1z"></path>
		</svg>`;

	GM_addStyle(`
		.gh-csc-wrap {
			position: relative;
		}
		.gh-csc-wrap:hover .gh-csc-button {
			display: block;
		}
		.gh-csc-button {
			display: none;
			padding: 3px 6px;
			position: absolute;
			top: 3px;
			right: 3px;
			z-index: 20;
		}
		.gh-csc-wrap.ghd-code-wrapper .gh-csc-button {
			right: 31px;
		}
		.gh-csc-button svg {
			vertical-align: text-bottom;
		}
	`);

	function addButton(wrap, code) {
		if (!wrap.classList.contains("gh-csc-wrap")) {
			copyId++;
			// See comments from sindresorhus/refined-github/issues/1278
			code.id = `gh-csc-${copyId}`;
			copyButton.setAttribute("for", `gh-csc-${copyId}`);
			wrap.classList.add("gh-csc-wrap");
			wrap.insertBefore(copyButton.cloneNode(true), wrap.childNodes[0]);
		}
	}

	function init() {
		const markdown = document.querySelector(markdownSelector);
		if (markdown) {
			[...document.querySelectorAll(markdownSelector)].forEach(md => {
				[...md.querySelectorAll(codeSelector)].forEach(pre => {
					let code = pre.querySelector("code");
					let wrap = pre.parentNode;
					if (code) {
						// pre > code
						addButton(pre, code);
					} else if (wrap.classList.contains("highlight")) {
						// div.highlight > pre
						addButton(wrap, pre);
					}
				});
			});
		}
	}

	document.addEventListener("ghmo:container", init);
	document.addEventListener("ghmo:comments", init);
	init();
})();


# CHMEX Notary Node Proposal 2019

## Voting Address ##
**Region: EU**
<img src="https://dexstats.info/upload/qrcode.png" align="right" height="150px" width="150px">

```
RChMex2FrLoqL3C3ED9tADfRBnUsUFJ4rj
```

<br>

# About me 
I am CHMEX Operator of <a href="https://dexstats.info" target="_blank">www.dexstats.info</a>, which provides various useful tools like `Trading History`, `Richlist & Lookup`, `Address Converter` and `PIRATE Migration & Onboarding` to name a few. Visit <a href="https://dexstats.info" target="_blank">dexstats.info</a> to learn more.
I work an DevOPS IT Job in Telco where I'm exposed to a lot of Data.

For the first time I would like to present myself as a candidate for Notary Node Election 2019 to operate a Node in the `EU Region`. **I only run for one Region with one Node**. In case of auto re-election in 2020 the proposed Use of Funds honored aswell.

# Why Vote for CHMEX - Dexstats

### ICO Contributor, Active Community Member since 2017, Team member since 2018. ###
#### Done. Running. #####
* Running <a href="https://dexstats.info" target="_blank">www.dexstats.info</a> and all it's Tools which you have maybe already used.<br>
* Running Fullnodes with about `4TB` of outbound data per month to help the network for all Notarized and known Assetchains<br>
* Hosting Hourly updated <a href="https://dexstats.info/richlist.php" target="_blank">Richlists</a>. Realtime <a href="https://explorer.dexstats.info"  target="_blank">Coinsupply</a> with API. Daily updated **<a href="https://dexstats.info/bootstrap.php"  target="_blank">Bootstraps</a>** on all Notarized Assetchains. Hosting about 50+ Explorers for Live and Testing Network https://explorer.dexstats.info . I got BarterDEX listed on CMC with integration.
* Hosting and maintaining API's to feed in Realtime _Blockfolio Coinfairvalue Blocktivity **CoinmarketCap** Coingecko Coinpaprika_ and others. Serving `4 Mio` API calls per day to these sites. That's `46 Req/s` or `1.4 Bil` Request per year.<br>
* Helping out People Migrate funds `1+Mio ARRR`, `1+ Mio USD` in NXT Assets saved. Trustee in OTC Transactions.
* Winner of the :beer:BEER&PIZZA:pizza: Atomic Swap contest in 2018. I will Airdrop `2 Mio` PIZZA-Testcoin to all my Voter regardless of the outcome of the Election! I was running LP Nodes on odd pairs like DBG/HUSH HUSH/VTC during bullmarket. I'm running PIZZA/BEER LP nodes. With mm2.0 these marketmaker Nodes will be activated again. My addresses have been involved in approx. 10% of all BarterDEX Atomic Swaps.
* I don't code C but some of my suggested RPC Calls have been implemented by James and Duke (_getsnapshot coinsupply convaddress_ to name a few.
* My <a href="https://dexstats.info/scale/index.html"  target="_blank">20k TPS / Visualization</a> was well Commented
* Maintaining and styled <a href="https://explorer.pirate.black"  target="_blank">https://explorer.pirate.black</a>
* I'm helping out people as much as I can on Discord and Telegram. A lot of time I test new KMD features.
* Onboarding System for PIRATE with Referral. https://pirate.dexstats.info

#### Upcoming #####
* I will continue creating Tools for the Community as needed. Dexstats needs a Redesign.
* Node will be running in Switzerland with a politically stable and Crypto Friendly Goverment. I believe in a **One Operator One Node** strategy.
* Integrated Richlist and Node List to Explorers.
* KMD Rewards Bot - It will notify you when Rewards stopp acccuring.
* Simple Fundraising Platform for Eco System Projects.

# Use of Funds:
* Increasing Infrastructer to all Regions :world_map:
* 10% of total mined KMD to LABS :microscope: ( min. 150 KMD per Month )
* 10% of total mined KMD to PIRATE :sailboat:	:anchor:	( min. 150 KMD per Month )
* Dedicating more time to the Komodo Eco System
* **If I get lucky to mine a big Block ( check: <a href="https://notarystats.info"  target="_blank">www.notarystats.info</a> ) with Reward >= 500KMD I will Airdrop 67% of it to my Voters (+10% to LABS, + 10% to PIRATE). These Big rewards should be for everybody.**
* minimum Funds are paid regardless of the KMD-FIAT Price.

If elected I can setup, run and pay more Servers and create new Tools I have a lot ideas, most importantly and `$BUIDL $BUIDL $BUIDL` for the next wave of Assetchains in 2019/2020.
I got some Donations from Community members over the last few month which I'm very thankful. With the current Infrastructer I pay around USD 250 per Month out of my pocket.

# Server Specs:
* Processor: `2x Xeon E5-2630v3 8x2.4 GHz` <img src="https://dexstats.info/upload/bunker-dc.png" align="right">
* RAM: `128 GB`
* Disk: `1TB SSD`
* Power: `2x Power Supply 100% Renewable Energy` :green_heart:
* Network: `1 Gbit Up and Down Link`
* Server Location: `Central Switzerland` _( Sidenote: 15m Underground in a ex-Military Bunker now Remodeled Datacenter )_

# Disclosure:
* I am an official Komodo Team Member (volunteering on partime base, not on payroll)
* PIRATE Member First Mate (Custodian of 250k. ARRR)
* <a href="http://kmd.explorer.dexstats.info/address/RF4HiVeuYpaznRPs7fkRAKKYqT5tuxQQTL" target="_blank">LABS</a> Node Operator, therefore have the capability to run a Notary Node.
* Not related or involved with any other Notary Node Operator or Candidate.
* To my current knowledge the location of my Node will be southern-most in Europe. I believe in a de-centralized network which I want to support this way.

# Contact:
* :iphone: Discord: `CHMEX#0686`
* :e-mail:: `chmex (@at@) dexstats.info`
* PGP Fingerprint: `8F9F41D44E98F84013E10F10780F6DE2576B2F6D`
## Thank you for reading my proposal and thank you for sending your Votes to

<img src="https://dexstats.info/upload/qrcode.png"  align="right" height="150px" width="150px">

```
RChMex2FrLoqL3C3ED9tADfRBnUsUFJ4rj
```

<br><br><br>



## PGP Public Key
```
-----BEGIN PGP PUBLIC KEY BLOCK-----
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
=dxt9
-----END PGP PUBLIC KEY BLOCK-----
```
