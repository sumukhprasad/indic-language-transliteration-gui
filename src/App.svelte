<script>
	const { ILTEngine } = require("./libilt/indic-language-transliteration/src/engine");
	const kannada = require('./libilt/indic-language-transliteration/src/schemes/kannada.js').scheme;
	const devanagari = require('./libilt/indic-language-transliteration/src/schemes/devanagari.js').scheme;

	var engine = new ILTEngine();	

	engine._loadScheme('kannada', kannada, false)
	engine._loadScheme('devanagari', devanagari, false)

	

	function updateAllTAs(t) {
	}
</script>

<head>
	<title>ILT-GUI</title>
</head>

<main>
	<h1>Indic Language Transliteration</h1>
	<a href="https://github.com/SumukhPrasad/indic-language-transliteration">github.com/SumukhPrasad/indic-language-transliteration</a>
	<table>
		<tr>
			<td>
				<select id="sch1">
				</select>
			</td>
			<td>
				<select id="sch2">
				</select>
			</td>
		</tr>
		<tr>
			<td><textarea id="sch1" on:keyup={updateAllTAs}></textarea></td>
			<td><textarea id="sch2" on:keyup={updateAllTAs}></textarea></td>
		</tr>
	</table>
</main>

<style>
	
</style>
