<script>
	let covers = [
		{
			imgSrc: "cover1.jpg",
			imgAlt: "A portrait of Margaret Cho and Atsuko Okatsuka",
			legend: "Margaret Cho",
			heir: "Atsuko Okatsuka",
			legendOccupation: "comedian and actress",
			heirOccupation: "comedian",
			articleLink: "https://www.nytimes.com/section/t-magazine",
			captionShowing: false,
		},
		{
			imgSrc: "cover2.jpg",
			imgAlt: "A portrait of Naomi Watts and Elle Fanning",
			legend: "Naomi Watts",
			heir: "Elle Fanning",
			legendOccupation: "actress",
			heirOccupation: "actress",
			articleLink: "https://www.nytimes.com/section/t-magazine",
			captionShowing: false,
		},
		{
			imgSrc: "cover3.jpg",
			imgAlt: "A portrait of Wu Tsang and Klein",
			legend: "Wu Tsang",
			heir: "Klein",
			legendOccupation: "multidisciplinary artist",
			heirOccupation: "musician & filmmaker",
			articleLink: "https://www.nytimes.com/section/t-magazine",
			captionShowing: false,
		},
		{
			imgSrc: "cover4.jpg",
			imgAlt: "A portrait of Salt-N-Pepa and Issa Rae",
			legend: "Salt-N-Pepa",
			heir: "Issa Rae",
			legendOccupation: "musicians",
			heirOccupation: "actress, producer, and screenwriter",
			articleLink: "https://www.nytimes.com/section/t-magazine",
			captionShowing: false,
		},
		{
			imgSrc: "cover5.jpg",
			imgAlt: "A portrait of Maria Grazia Chiuri and Zadie Xa",
			legend: "Maria Grazia Chiuri",
			heir: "Zadie Xa",
			legendOccupation: "fasion designer",
			heirOccupation: "interdisciplinary artist",
			articleLink: "https://www.nytimes.com/section/t-magazine",
			captionShowing: false,
		},
		{
			imgSrc: "cover6.jpg",
			imgAlt: "A portrait of Joan Baez and Lana Del Rey",
			legend: "Joan Baez",
			heir: "Lana Del Rey",
			legendOccupation: "singer-songwriter & visual artist",
			heirOccupation: "singer-songwriter",
			articleLink: "https://www.nytimes.com/section/t-magazine",
			captionShowing: false,
		},
	];
	let animationPlayState = "running";
	// function pauseAnimation() {

	// }
	// function playAnimation() {

	// }
	function showLabel(i) {
		covers[i].captionShowing = true;
		console.log("show label");
		animationPlayState = "paused";
	}
	function hideLabel(i) {
		covers[i].captionShowing = false;
		console.log("hide label");
		animationPlayState = "running";
	}
	let mx = "0px";
	let my = "0px";
	function handleMousemove(event) {
		mx = `${event.clientX}px`;
		my = `${event.clientY - 10}px`;
		console.log(mx, my);
	}
</script>

<section
	class="wrapper"
	style="--animation-play-state: {animationPlayState}; --cursor-x: {mx}; --cursor-y: {my}"
>
	<a href="https://www.nytimes.com/section/t-magazine">
		<div class="t-mag-logo"><img src="t-logo.svg" /></div>
	</a>
	<div class="header">
		<a href="https://www.nytimes.com/section/t-magazine">
			<div class="title"><img src="handwriting.svg" /></div>
		</a>
		<div class="dek">
			40 legendary female artists—<br />and the younger women who remind them of
			<br />why they make art.
		</div>
	</div>

	<div class="scroll-images-wrapper">
		<div class="images-wrapper-1">
			{#each covers as cover, i}
				<a href={cover.articleLink}>
					<div
						class="cover-wrapper"
						on:mouseover={() => showLabel(i)}
						on:focus={() => showLabel(i)}
						on:blur={() => hideLabel(i)}
						on:mouseleave={() => hideLabel(i)}
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
						on:mouseover={() => showLabel(i)}
						on:focus={() => showLabel(i)}
						on:blur={() => hideLabel(i)}
						on:mouseleave={() => hideLabel(i)}
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
	<div class="link"><a href="https://www.google.com">READ THE ISSUE</a></div>
</section>

<style>
	a {
		text-decoration: none;
		color: inherit;
	}
	.wrapper {
		display: flex;
		position: relative;
		flex-direction: column;
		align-items: center;
		padding: 30px;
		border-top: 1px solid black;
		border-bottom: 1px solid black;
		background-color: #eeeeee;
	}
	.title {
		width: 600px;
	}
	.title img {
		width: 100%;
		height: auto;
	}
	.t-mag-logo {
		position: absolute;
		top: 30px;
		left: 30px;
	}
	.dek {
		text-align: center;
		font-family: "FactCondensedMedium";
		font-size: 24px;
		margin-bottom: 50px;
	}
	.link {
		font-family: "KipBold";
		margin-top: 30px;
	}
	.images-wrapper-1 {
		display: flex;
		position: absolute;
		left: 0%;
		top: 0%;
		animation: primary 14s linear infinite;
		animation-play-state: var(--animation-play-state);
	}
	.images-wrapper-2 {
		display: flex;
		position: absolute;
		left: 0%;
		top: 0%;
		animation: secondary 14s linear infinite;
		animation-play-state: var(--animation-play-state);
	}
	.images-wrapper-1 img,
	.images-wrapper-2 img {
		width: calc(100vw / 6);
		height: auto;
		cursor: pointer;
	}
	.scroll-images-wrapper {
		position: relative;
		width: 100vw;
		height: calc((100vw / 6) * 3450 / 2850);
		overflow-x: hidden;
	}
	/* .cover-wrapper {
		position: relative;
	} */
	.label {
		white-space: nowrap;
		background-color: white;
		border: black 1px dotted;
		padding-top: 8px;
		padding-bottom: 5px;
		padding-left: 10px;
		padding-right: 10px;
		font-size: 16px;
		line-height: 1;
		text-align: center;
		text-transform: uppercase;
		position: fixed;
		transform: translate(-50%, -100%);
		top: var(--cursor-y);
		left: var(--cursor-x);
		z-index: 100;
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
	@keyframes primary {
		from {
			left: 0%;
		}
		to {
			left: -100%;
		}
	}
	@keyframes secondary {
		from {
			left: 100%;
		}
		to {
			left: 0%;
		}
	}
</style>
