<script>
	let covers = [
		{
			imgSrc: "cover1.jpg",
			imgAlt: "A portrait of Margaret Cho and Atsuko Okatsuka",
			legend: "Margaret Cho",
			heir: "Atsuko Okatsuka",
			legendOccupation: "comedian and actress",
			heirOccupation: "comedian",
			articleLink:
				"https://www.nytimes.com/2023/04/20/t-magazine/margaret-cho-atsuko-okatsuka.html",
			captionShowing: false,
		},
		{
			imgSrc: "cover2.jpg",
			imgAlt: "A portrait of Naomi Watts and Elle Fanning",
			legend: "Naomi Watts",
			heir: "Elle Fanning",
			legendOccupation: "actress",
			heirOccupation: "actress",
			articleLink:
				"https://www.nytimes.com/2023/04/20/t-magazine/naomi-watts-elle-fanning.html",
			captionShowing: false,
		},
		{
			imgSrc: "cover3.jpg",
			imgAlt: "A portrait of Wu Tsang and Klein",
			legend: "Wu Tsang",
			heir: "Klein",
			legendOccupation: "multidisciplinary artist",
			heirOccupation: "musician & filmmaker",
			articleLink:
				"https://www.nytimes.com/2023/04/20/t-magazine/wu-tsang-klein.html",
			captionShowing: false,
		},
		{
			imgSrc: "cover4.jpg",
			imgAlt: "A portrait of Salt-N-Pepa and Issa Rae",
			legend: "Salt-N-Pepa",
			heir: "Issa Rae",
			legendOccupation: "musicians",
			heirOccupation: "actress, producer, and screenwriter",
			articleLink:
				"https://www.nytimes.com/2023/04/20/t-magazine/salt-n-pepa-issa-rae.html",
			captionShowing: false,
		},
		{
			imgSrc: "cover5.jpg",
			imgAlt: "A portrait of Maria Grazia Chiuri and Zadie Xa",
			legend: "Maria Grazia Chiuri",
			heir: "Zadie Xa",
			legendOccupation: "fasion designer",
			heirOccupation: "interdisciplinary artist",
			articleLink:
				"https://www.nytimes.com/2023/04/20/t-magazine/maria-grazia-chiuri-zadie-xa.html",
			captionShowing: false,
		},
		{
			imgSrc: "cover6.jpg",
			imgAlt: "A portrait of Joan Baez and Lana Del Rey",
			legend: "Joan Baez",
			heir: "Lana Del Rey",
			legendOccupation: "singer-songwriter & visual artist",
			heirOccupation: "singer-songwriter",
			articleLink:
				"https://www.nytimes.com/2023/04/20/t-magazine/lana-del-rey-joan-baez.html",
			captionShowing: false,
		},
	];
	let animationPlayState = "running";
	let mx = "0px";
	let my = "0px";
	function handleImgMouseover(i) {
		if (window.matchMedia("(min-width: 501px)").matches) {
			covers[i].captionShowing = true;
			animationPlayState = "paused";
		}
	}
	function handleImgMouseleave(i) {
		if (window.matchMedia("(min-width: 501px)").matches) {
			covers[i].captionShowing = false;
			animationPlayState = "running";
		}
	}
	function handleMousemove(event) {
		if (window.matchMedia("(min-width: 501px)").matches) {
			mx = `${event.clientX}px`;
			my = `${event.clientY - 10}px`;
		}
	}
</script>

<section
	class="wrapper"
	style="--animation-play-state: {animationPlayState}; --cursor-x: {mx}; --cursor-y: {my}"
>
	<a href="https://www.nytimes.com/section/t-magazine">
		<img alt="T Magazine logo" class="t-mag-logo" src="t-logo.svg" />
	</a>
	<div class="header">
		<a
			href="https://www.nytimes.com/interactive/2023/04/20/t-magazine/women-artists-culture-mentors"
		>
			<div class="title">
				<img
					alt="handwritten logo for this issue of T Magazine - reads 'A Woman's Work'"
					src="handwriting.svg"
				/>
			</div>
		</a>
		<div class="dek">
			40 legendary female artists—<br />and the younger women who remind them of
			<br />why they make art.
		</div>
	</div>

	<!-- Separate mobile + desktop carousels because of link + hover interaction discrepancy -->

	<!-- MOBILE IMAGE CAROUSEL -->
	<div class="scroll-images-wrapper mobile">
		<a
			href="https://www.nytimes.com/interactive/2023/04/20/t-magazine/women-artists-culture-mentors"
		>
			<div class="images-wrapper-1">
				{#each covers as cover, i}
					<div class="cover-wrapper">
						<div
							class="label"
							style={cover.captionShowing ? `display: block` : `display: none`}
						>
							<span class="legend-type">{`${cover.legend}, `}</span>
							<span class="subtitle-type">{`${cover.legendOccupation}`}</span>
							<br />
							<span class="subtitle-type">and&nbsp;</span><span
								class="heir-type">{`${cover.heir}, `}</span
							><span class="subtitle-type">{`${cover.heirOccupation}`}</span>
						</div>
						<img src={cover.imgSrc} alt={cover.imgAlt} />
					</div>
				{/each}
			</div>
			<div class="images-wrapper-2">
				{#each covers as cover, i}
					<div class="cover-wrapper">
						<div
							class="label"
							style={cover.captionShowing ? `display: block` : `display: none`}
						>
							<span class="legend-type">{`${cover.legend}, `}</span>
							<span class="subtitle-type">{`${cover.legendOccupation}`}</span>
							<br />
							<span class="subtitle-type">and&nbsp;</span><span
								class="heir-type">{`${cover.heir}, `}</span
							><span class="subtitle-type">{`${cover.heirOccupation}`}</span>
						</div>
						<img src={cover.imgSrc} alt={cover.imgAlt} />
					</div>
				{/each}
			</div>
		</a>
	</div>

	<!-- DESKTOP IMAGE CAROUSEL -->
	<div class="scroll-images-wrapper desktop">
		<div class="images-wrapper-1">
			{#each covers as cover, i}
				<a href={cover.articleLink}>
					<div
						class="cover-wrapper"
						on:mouseover={() => handleImgMouseover(i)}
						on:focus={() => handleImgMouseover(i)}
						on:blur={() => handleImgMouseleave(i)}
						on:mouseleave={() => handleImgMouseleave(i)}
						on:mousemove={handleMousemove}
					>
						<div
							class="label"
							style={cover.captionShowing ? `display: block` : `display: none`}
						>
							<span class="legend-type">{`${cover.legend}, `}</span>
							<span class="subtitle-type">{`${cover.legendOccupation}`}</span>
							<br />
							<span class="subtitle-type">and&nbsp;</span><span
								class="heir-type">{`${cover.heir}, `}</span
							><span class="subtitle-type">{`${cover.heirOccupation}`}</span>
						</div>
						<img src={cover.imgSrc} alt={cover.imgAlt} />
					</div>
				</a>
			{/each}
		</div>
		<div class="images-wrapper-2">
			{#each covers as cover, i}
				<a href={cover.articleLink}>
					<div
						class="cover-wrapper"
						on:mouseover={() => handleImgMouseover(i)}
						on:focus={() => handleImgMouseover(i)}
						on:blur={() => handleImgMouseleave(i)}
						on:mouseleave={() => handleImgMouseleave(i)}
						on:mousemove={handleMousemove}
					>
						<div
							class="label"
							style={cover.captionShowing ? `display: block` : `display: none`}
						>
							<span class="legend-type">{`${cover.legend}, `}</span>
							<span class="subtitle-type">{`${cover.legendOccupation}`}</span>
							<br />
							<span class="subtitle-type">and&nbsp;</span><span
								class="heir-type">{`${cover.heir}, `}</span
							><span class="subtitle-type">{`${cover.heirOccupation}`}</span>
						</div>
						<img src={cover.imgSrc} alt={cover.imgAlt} />
					</div>
				</a>
			{/each}
		</div>
	</div>
	<!-- DANNY - can you add the link to the interactive here? -->
	<a href="https://www.google.com" class="link">READ THE ISSUE</a>
</section>

<style>
	/* SMALL  */
	@media only screen and (max-width: 500px) {
		.scroll-images-wrapper.desktop {
			display: none;
		}
		.title {
			width: 100%;
		}
		.t-mag-logo {
			position: absolute;
			top: 20px;
			left: 20px;
			width: 90px;
			height: auto;
		}
		.wrapper {
			padding: 10px;
			padding-bottom: 0px;
			padding-top: 130px;
		}
		.dek {
			font-size: 5vw;
			margin-bottom: 20px;
		}
		.link {
			margin-top: 15px;
			margin-bottom: 15px;
		}
		.images-wrapper-1 img,
		.images-wrapper-2 img {
			width: calc(100vw / 2);
			height: auto;
			cursor: pointer;
		}
		.scroll-images-wrapper {
			height: calc((100vw / 2) * 3450 / 2850);
		}
		.images-wrapper-1 {
			animation: primary-mobile 20s linear infinite;
		}
		.images-wrapper-2 {
			animation: secondary-mobile 20s linear infinite;
		}
	}
	/* MEDIUM */
	@media only screen and (min-width: 501px) and (max-width: 850px) {
		.scroll-images-wrapper.mobile {
			display: none;
		}
		.title {
			width: 100%;
			max-width: 500px;
			display: flex;
			justify-content: center;
		}
		.t-mag-logo {
			position: absolute;
			top: 20px;
			left: 20px;
			width: 90px;
			height: auto;
		}
		.wrapper {
			padding: 10px;
			padding-bottom: 0px;
			padding-top: 100px;
		}
		.dek {
			font-size: 22px;
			margin-bottom: 20px;
		}
		.link {
			margin-top: 30px;
			margin-bottom: 30px;
		}
		.images-wrapper-1 img,
		.images-wrapper-2 img {
			width: calc(100vw / 3);
			height: auto;
			cursor: pointer;
		}
		.scroll-images-wrapper {
			height: calc((100vw / 3) * 3450 / 2850);
		}
		.images-wrapper-1 {
			animation: primary-tablet 20s linear infinite;
		}
		.images-wrapper-2 {
			animation: secondary-tablet 20s linear infinite;
		}
	}
	/* LARGE */
	@media only screen and (min-width: 851px) {
		.scroll-images-wrapper.mobile {
			display: none;
		}
		.title {
			width: 600px;
		}
		.t-mag-logo {
			position: absolute;
			top: 30px;
			left: 30px;
			width: 100px;
			height: auto;
		}
		.wrapper {
			padding: 15px;
		}
		.dek {
			font-size: 24px;
			margin-bottom: 50px;
		}
		.link {
			margin-top: 30px;
			margin-bottom: 15px;
		}
		.images-wrapper-1 img,
		.images-wrapper-2 img {
			width: calc(100vw / 6);
			height: auto;
			cursor: pointer;
		}
		.scroll-images-wrapper {
			height: calc((100vw / 6) * 3450 / 2850);
		}
		.images-wrapper-1 {
			animation: primary-desktop 14s linear infinite;
		}
		.images-wrapper-2 {
			animation: secondary-desktop 14s linear infinite;
		}
	}
	/* GLOBAL */
	* {
		-webkit-font-smoothing: antialiased;
		-moz-osx-font-smoothing: grayscale;
	}
	:global(body) {
		padding: 0px !important;
		margin: 0px !important;
	}
	a {
		text-decoration: none;
		color: inherit;
	}
	.wrapper {
		display: flex;
		position: relative;
		flex-direction: column;
		align-items: center;
		border-top: 1px solid black;
		border-bottom: 1px solid black;
		background: linear-gradient(
			180deg,
			#dd5434 0%,
			#e19f4e 21.18%,
			#ffe64c 100%
		);
	}
	.title img {
		width: 100%;
		height: auto;
	}
	.dek {
		font-family: "FactCondensedMedium";
		text-align: center;
	}
	.link {
		font-family: "KipBold";
	}
	.images-wrapper-1 {
		display: flex;
		position: absolute;
		left: 0%;
		top: 0%;
		animation-play-state: var(--animation-play-state);
	}
	.images-wrapper-2 {
		display: flex;
		position: absolute;
		left: 0%;
		top: 0%;
		animation-play-state: var(--animation-play-state);
	}
	.scroll-images-wrapper {
		position: relative;
		width: 100vw;
		overflow-x: hidden;
	}
	.label {
		position: fixed;
		top: var(--cursor-y);
		left: var(--cursor-x);
		transform: translate(-50%, -100%);
		z-index: 100;
		padding-top: 8px;
		padding-bottom: 5px;
		padding-left: 10px;
		padding-right: 10px;
		background-color: white;
		border: black 1px dotted;
		font-size: 16px;
		line-height: 1;
		text-align: center;
		text-transform: uppercase;
		white-space: nowrap;
	}
	.legend-type {
		font-family: "KipCondensedBold";
	}
	.heir-type {
		font-family: "FactCondensedBold";
	}
	.subtitle-type {
		font-family: "KipCondensedRegular";
		font-size: 12px;
	}
	.link:hover {
		text-decoration: underline !important;
	}
	@keyframes primary-desktop {
		from {
			left: 0%;
		}
		to {
			left: -100%;
		}
	}
	@keyframes secondary-desktop {
		from {
			left: 100%;
		}
		to {
			left: 0%;
		}
	}
	@keyframes primary-tablet {
		from {
			left: 0%;
		}
		to {
			left: -200%;
		}
	}
	@keyframes secondary-tablet {
		from {
			left: 200%;
		}
		to {
			left: 0%;
		}
	}
	@keyframes primary-mobile {
		from {
			left: 0%;
		}
		to {
			left: -300%;
		}
	}
	@keyframes secondary-mobile {
		from {
			left: 300%;
		}
		to {
			left: 0%;
		}
	}
	@font-face {
		font-family: "FactCondensedMedium";
		src: url("/Fact Deck-67 Condensed Medium.otf") format("opentype");
	}
	@font-face {
		font-family: "FactCondensedBold";
		src: url("/Fact Deck-77 Condensed Bold.otf") format("opentype");
	}
	@font-face {
		font-family: "KipCondensedRegular";
		src: url("/Kippenberger-57 Condensed Regular.otf") format("opentype");
	}
	@font-face {
		font-family: "KipBold";
		src: url("/Kippenberger-75 Bold.otf") format("opentype");
	}
	@font-face {
		font-family: "KipCondensedBold";
		src: url("/Kippenberger-77 Condensed Bold.otf") format("opentype");
	}
</style>
