### <a name="wpf-datatemplate-elements-are-now-visible-to-uia"></a>Elementos DataTemplate do WPF agora são visíveis à UIA

|   |   |
|---|---|
|Detalhes|Anteriormente, os elementos <xref:System.Windows.DataTemplate?displayProperty=name> eram invisíveis à Automação da Interface do Usuário. A partir da versão 4.5, a Automação da Interface do Usuário detectar esses elementos. Isso é útil em muitos casos, mas pode arruinar os testes que dependem das árvores UIA que não contêm elementos <xref:System.Windows.DataTemplate?displayProperty=name>.|
|Sugestão|Os testes de Automação da Interface do Usuário para esse aplicativo talvez precisem ser atualizados para contabilizar a árvore UIA agora, incluindo elementos <xref:System.Windows.DataTemplate?displayProperty=name> anteriormente invisíveis. Por exemplo, os testes que esperam que alguns elementos fiquem próximos uns dos outros agora podem precisar esperar elementos UIA anteriormente invisíveis entre eles. Ou os testes que dependem de determinadas contagens ou de índices para elementos UIA talvez precisem ser atualizados com novos valores.|
|Escopo|Microsoft Edge|
|Versão|4.5|
|Tipo|Tempo de execução|
|APIs afetadas|<ul><li><xref:System.Windows.DataTemplate.%23ctor?displayProperty=nameWithType></li><li><xref:System.Windows.DataTemplate.%23ctor(System.Object)?displayProperty=nameWithType></li></ul>|

