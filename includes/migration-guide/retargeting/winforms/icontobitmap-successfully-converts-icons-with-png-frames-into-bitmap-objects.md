### <a name="icontobitmap-successfully-converts-icons-with-png-frames-into-bitmap-objects"></a>Icon.ToBitmap converte com êxito ícones com quadros PNG em objetos Bitmap

|   |   |
|---|---|
|Detalhes|A partir dos aplicativos destinados ao .NET Framework 4.6, o método <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> converte com êxito ícones com quadros PNG em objetos Bitmap. Em aplicativos destinados ao .NET Framework 4.5.2 e versões anteriores, o método <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> gera uma exceção <xref:System.ArgumentOutOfRangeException> se o objeto Icon tiver quadros PNG. Essa alteração afeta aplicativos recompilados para serem destinados ao .NET Framework 4.6 e que implementam um tratamento especial para o <xref:System.ArgumentOutOfRangeException> que é lançado quando um objeto Icon tem quadros PNG. Ao executar no .NET Framework 4.6, a conversão é bem-sucedida, uma <xref:System.ArgumentOutOfRangeException> não é mais gerada e, portanto, o manipulador de exceção não é invocado.|
|Sugestão|Se esse comportamento for indesejável, será possível reter o comportamento anterior adicionando o seguinte elemento à seção <code>&lt;runtime&gt;</code> do arquivo app.config:<pre><code class="language-xml">&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Drawing.DontSupportPngFramesInIcons=true&quot; /&gt;&#13;&#10;</code></pre>Se o arquivo app.config já contiver o elemento <code>AppContextSwitchOverrides</code>, o novo valor deverá ser mesclado ao atributo de valor, da seguinte forma:<pre><code class="language-xml">&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Drawing.DontSupportPngFramesInIcons=true;&lt;previous key&gt;=&lt;previous value&gt;&quot; /&gt;&#13;&#10;</code></pre>|
|Escopo|Secundário|
|Versão|4.6|
|Tipo|Redirecionando|
|APIs afetadas|<ul><li><xref:System.Drawing.Icon.ToBitmap?displayProperty=nameWithType></li></ul>|

