### <a name="corprfgcroothandles-are-not-being-enumerated-by-profilers"></a>COR_PRF_GC_ROOT_HANDLEs não estão sendo enumerados por criadores de perfil

|   |   |
|---|---|
|Detalhes|No .NET Framework v4.5.1, a API de criação de perfil <code>RootReferences2()</code>, de maneira incorreta, nunca retorna <code>COR_PRF_GC_ROOT_HANDLE</code> (que, em vez disso, é retornada como <code>COR_PRF_GC_ROOT_OTHER</code>). Esse problema foi corrigido a partir do .NET Framework 4.6.|
|Sugestão|Esse problema foi corrigido no .NET Framework 4.6 e pode ser resolvido com o upgrade para essa versão do .NET Framework.|
|Escopo|Secundário|
|Versão|4.5.1|
|Tipo|Tempo de execução|

