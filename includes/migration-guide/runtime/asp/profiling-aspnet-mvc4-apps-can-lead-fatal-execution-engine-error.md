### <a name="profiling-aspnet-mvc4-apps-can-lead-to-fatal-execution-engine-error"></a>Aplicativos ASP.NET MVC4 de criação de perfil podem causar Erro Fatal do Mecanismo de Execução

|   |   |
|---|---|
|Detalhes|Os criadores de perfil que usam NGEN/assemblies de perfil podem causar pane em aplicativos ASP.NET MVC4 de criação de perfil na inicialização com o "Erro Fatal do Mecanismo de Execução".|
|Sugestão|Esse problema foi corrigido no .NET Framework 4.5.2. Como alternativa, o criador de perfil pode evitar esse problema especificando <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> em sua máscara de evento.|
|Escopo|Microsoft Edge|
|Versão|4.5|
|Tipo|Tempo de execução|

