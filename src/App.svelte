<script>
	const { ILTEngine } = require("./libilt/indic-language-transliteration/src/engine");

	

	const schemes = ["devanagari", "iast", "itrans", "kannada", "malayalam", "oriya", "tamil", "telugu", "velthuis"];


	function updateToBox() {
		var engine = new ILTEngine();	

		var from = document.getElementById('from').value;
		var to = document.getElementById('to').value;

		const fromSchemeObj = require(`./libilt/indic-language-transliteration/src/schemes/${from}`);
		const toSchemeObj = require(`./libilt/indic-language-transliteration/src/schemes/${to}`);

		engine._loadScheme(from, fromSchemeObj.scheme, fromSchemeObj.isRoman)
		engine._loadScheme(to, toSchemeObj.scheme, toSchemeObj.isRoman)
		
		document.getElementById('toarea').value = engine.autoTransliterate(document.getElementById('fromarea').value, from, to)
	}
</script>

<head>
	<title>ILT-GUI</title>
</head>

<main>
	<h1>Indic Language Transliteration</h1>
	<table>
		<tr>
			<td>
				From <select id="from" on:change={updateToBox}>
					{#each schemes as scheme}
						<option>{scheme}</option>
					{/each}
				</select> ...
			</td>
			<td>
				... to <select id="to" on:change={updateToBox}>
					{#each schemes as scheme}
						<option>{scheme}</option>
					{/each}
				</select>
			</td>
		</tr>
		<tr>
			<td><textarea id="fromarea" on:keyup={updateToBox}></textarea></td>
			<td><textarea id="toarea" readonly></textarea></td>
		</tr>
	</table>

	<a href="https://github.com/SumukhPrasad/indic-language-transliteration">github.com/SumukhPrasad/indic-language-transliteration</a>
</main>

<style>
	
</style>
