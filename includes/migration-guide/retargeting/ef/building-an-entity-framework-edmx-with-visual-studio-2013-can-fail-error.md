### <a name="building-an-entity-framework-edmx-with-visual-studio-2013-can-fail-with-error-msb4062-if-using-the-entitydeploysplit-or-entityclean-tasks"></a>A compilação de um edmx do Entity Framework com o Visual Studio 2013 pode falhar com o erro MSB4062 se estiver usando as tarefas EntityDeploySplit ou EntityClean

|   |   |
|---|---|
|Detalhes|As ferramentas do MSBuild 12.0 (incluídas no Visual Studio 2013) alteraram os locais do arquivo MSBuild, fazendo com que arquivos de destino do Entity Framework sejam inválidos. O resultado é que as tarefas <code>EntityDeploySplit</code> e <code>EntityClean</code> falham porque não conseguem localizar <code>Microsoft.Data.Entity.Build.Tasks.dll</code>. Observe que essa interrupção se deve a uma alteração no conjunto de ferramentas (MSBuild/VS), e não por uma mudança no .NET Framework. Ela ocorrerá apenas no upgrade das ferramentas do desenvolvedor, não simplesmente no upgrade do .NET Framework.|
|Sugestão|Os arquivos de destino do Entity Framework foram corrigidos para trabalhar com o novo layout do MSBuild a partir do .NET Framework 4.6. O upgrade para essa versão do Framework corrigirá esse problema. Como alternativa, [esta](http://stackoverflow.com/a/24249247/131944) solução alternativa pode ser usada para aplicar patches diretamente aos arquivos de destino.|
|Escopo|Principal|
|Versão|4.5.1|
|Tipo|Redirecionando|

