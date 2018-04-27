### <a name="incorrect-implementation-of-memberdescriptorequals"></a>Implementação incorreta de MemberDescriptor.Equals

|   |   |
|---|---|
|Detalhes|A implementação original do método &quot;Equals&quot; comparava duas propriedades de cadeia de caracteres diferentes dos objetos em comparação: nome da categoria com a cadeia de caracteres de descrição. A correção compara a &quot;categoria&quot; do primeiro objeto à &quot;categoria&quot; do segundo, e a &quot;descrição&quot; à &quot;descrição&quot;. O valor da configuração MemberDescriptorEqualsReturnsFalseIfEquivalent pode ser definido como true para recusar o novo comportamento se destinado ao 4.6.2 ou como false para habilitar essa correção quando o destino for uma versão de estrutura abaixo da 4.6.2.|
|Sugestão|Se seu aplicativo depender de MemberDescriptor.Equals, às vezes, retornar “false" quando descritores forem equivalentes e seu destino for a versão 4.6.2 do .NET Framework, você tem várias opções:<ol><li>Fazer alterações de código para comparar os campos &quot;categoria&quot; e &quot;descrição&quot; manualmente além de executar o método Equals.</li><li>Recusar essa alteração adicionando o seguinte valor ao arquivo app.config:</li></ol><pre><code class="language-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.MemberDescriptorEqualsReturnsFalseIfEquivalent=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Se seu aplicativo for destinado à versão 4.6.1 ou anterior do .NET Framework e você quiser que essa alteração seja habilitada, será possível definir a opção de compatibilidade como false adicionando o seguinte valor ao arquivo app.config:<pre><code class="language-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.MemberDescriptorEqualsReturnsFalseIfEquivalent=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Escopo|Microsoft Edge|
|Versão|4.6.2|
|Tipo|Redirecionando|
|APIs afetadas|<ul><li><xref:System.ComponentModel.MemberDescriptor.Equals(System.Object)?displayProperty=nameWithType></li></ul>|

