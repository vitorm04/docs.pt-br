### <a name="resizing-a-grid-can-hang"></a>Redimensionar uma grade pode causar travamento

|   |   |
|---|---|
|Detalhes|Um loop infinito pode ocorrer durante o layout de um <code>T:System.Windows.Controls.Grid</code> nas seguintes circunstâncias:<ul><li>As definições de linha contêm dois *-rows, ambos declarando um MinHeight e um MaxHeight.</li><li>O conteúdo dos *-rows não ultrapassa o MaxHeight correspondente</li><li>A altura disponível da grade é ultrapassada pelo primeiro MinHeight (além de qualquer outra linha fixa ou automática)</li><li>O aplicativo é destinado ao .Net 4.7 ou aceita o algoritmo de alocação do 4.7 definindo <code>Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=false</code></li></ul>O loop também aconteceria com mais de duas linhas ou no caso análogo para colunas. O problema foi corrigido no .Net 4.7.1.|
|Sugestão|Atualizar para .Net 4.7.1.  Como alternativa, se não precisar do algoritmo de alocação do 4.7, você poderá usar a seguinte configuração:<pre><code class="language-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Escopo|Microsoft Edge|
|Versão|4.7|
|Tipo|Tempo de execução|

