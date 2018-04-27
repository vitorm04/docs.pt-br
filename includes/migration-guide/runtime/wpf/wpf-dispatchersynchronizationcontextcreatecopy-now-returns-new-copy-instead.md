### <a name="wpf-dispatchersynchronizationcontextcreatecopy-now-returns-a-new-copy-instead-of-the-current-instance"></a>DispatcherSynchronizationContext.CreateCopy do WPF agora retorna uma nova cópia em vez da instância atual

|   |   |
|---|---|
|Detalhes|No .NET Framework 4, <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> retornava uma referência à instância atual, basicamente como uma otimização de desempenho. No .NET Framework 4.5, ele retorna uma nova instância que possibilita, pela primeira vez, concluir que referências iguais indicam que o thread em execução está no contexto de sincronização correto.  É provável que o código que verifica a identidade dessas referências seja afetado, mas, por causa da alteração, o código que chama <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> deve ser testado como parte da migração para o .NET Framework 4.5 ou mais recente.|
|Sugestão|Lembre-se de que <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> agora retornará um novo objeto <xref:System.Threading.SynchronizationContext?displayProperty=name>. Antigamente, o código que usava equivalência de referências gerada dessa maneira não era de fato verificado se estava no contexto apropriado, mas agora o é quando compilado no .NET 4.5 ou mais recente.  Embora não haja probabilidade de causar problemas, praticar os caminhos de código afetados deve ser suficiente para determinar se isso impõe algum problema.|
|Escopo|Secundário|
|Versão|4.5|
|Tipo|Tempo de execução|
|APIs afetadas|<ul><li><xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy?displayProperty=nameWithType></li></ul>|

