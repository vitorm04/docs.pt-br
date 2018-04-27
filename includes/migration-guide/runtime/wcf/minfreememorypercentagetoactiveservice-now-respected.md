### <a name="minfreememorypercentagetoactiveservice-is-now-respected"></a>MinFreeMemoryPercentageToActiveService agora é respeitado

|   |   |
|---|---|
|Detalhes|Essa configuração estabelece a memória mínima que deve estar disponível no servidor para que um serviço WCF possa ser ativado. Ela foi projetada para evitar exceções <xref:System.OutOfMemoryException?displayProperty=name>. No .NET Framework 4.5, essa configuração não tinha nenhum efeito. No .NET Framework 4.5.1, essa configuração é observada.|
|Sugestão|Ocorrerá uma exceção se a memória livre disponível no servidor Web for menor que a porcentagem definida pela definição de configuração. Alguns serviços WCF iniciados com êxito e executados em um ambiente de memória restrito agora podem falhar.|
|Escopo|Secundário|
|Versão|4.5.1|
|Tipo|Tempo de execução|

