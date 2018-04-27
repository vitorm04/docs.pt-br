### <a name="no-longer-able-to-set-enableviewstatemac-to-false"></a>Não é mais possível definir EnableViewStateMac como false

|   |   |
|---|---|
|Detalhes|O ASP.NET não permite mais que os desenvolvedores especifiquem <code>&lt;pages enableViewStateMac=&quot;false&quot;/&gt;</code> ou <code>&lt;@Page EnableViewStateMac=&quot;false&quot; %&gt;</code>. O MAC (Message Authentication Code) de estado da exibição agora é obrigatório em todas as solicitações com estado de exibição embutido. Apenas aplicativos que definiram explicitamente a propriedade EnableViewStateMac como <code>false</code> são afetados.|
|Sugestão|EnableViewStateMac deve ser considerada true e qualquer erro MAC resultante deverá ser resolvido (conforme explicado [nestas diretrizes](https://support.microsoft.com/kb/2915218), que contêm várias resoluções que variam de acordo com as características do que está causando os erros MAC).|
|Escopo|Principal|
|Versão|4.5.2|
|Tipo|Tempo de execução|

