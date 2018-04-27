### <a name="tabcontrol-selectionchanged-event-and-selectedcontent-property"></a>Evento TabControl SelectionChanged e propriedade SelectedContent

|   |   |
|---|---|
|Detalhes|A partir do .NET Framework 4.7.1, um <xref:System.Windows.Controls.TabControl> atualiza o valor de sua propriedade <xref:System.Windows.Controls.TabControl.SelectedContent> antes de acionar o evento <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged>, quando sua seleção é alterada. No .NET Framework 4.7 e em versões anteriores, a atualização de SelectedContent acontecia depois do evento.|
|Sugestão|Aplicativos destinados ao .NET Framework 4.7.1 ou posteriores podem recusar essa alteração e usar o comportamento herdado adicionando o seguinte à seção <code>&lt;runtime&gt;</code> do arquivo de configuração de aplicativo:<pre><code class="language-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.TabControl.SelectionPropertiesCanLagBehindSelectionChangedEvent=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Aplicativos destinados ao .NET Framework 4.7 ou anteriores, mas que são executados no .NET Framework 4.7.1 ou posteriores podem habilitar o novo comportamento adicionando a seguinte linha à seção <code>&lt;runtime&gt;</code> do arquivo de configuração de aplicativo:<pre><code class="language-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.TabControl.SelectionPropertiesCanLagBehindSelectionChangedEvent=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Escopo|Secundário|
|Versão|4.7.1|
|Tipo|Redirecionando|
|APIs afetadas|<ul><li><xref:System.Windows.Controls.TabControl.SelectedContent?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.Primitives.Selector.SelectionChanged?displayProperty=nameWithType></li></ul>|

