### <a name="resolveassemblyreference-task-now-warns-of-dependencies-with-the-wrong-architecture"></a>A tarefa ResolveAssemblyReference agora avisa sobre dependências com arquitetura incorreta

|   |   |
|---|---|
|Detalhes|A tarefa emite um aviso, MSB3270, que indica que uma referência ou qualquer uma de suas dependências não corresponde à arquitetura do aplicativo. Por exemplo, isso ocorrerá se um aplicativo que tenha sido compilado com a opção <code>AnyCPU</code> incluir uma referência x86. Esse cenário pode resultar em uma falha do aplicativo no tempo de execução (nesse caso, se o aplicativo for implantado como um processo x64).|
|Sugestão|Há duas áreas de impacto:<ul><li>A recompilação gerencia os avisos que não foram exibidos quando o aplicativo foi compilado com uma versão anterior do MSBuild. Entretanto, como o aviso identifica uma possível fonte de falha no tempo de execução, ele deve ser investigado e resolvido.</li><li>Se os avisos forem tratados como erros, o aplicativo não será compilado.</li></ul>|
|Escopo|Secundário|
|Versão|4.5.1|
|Tipo|Redirecionando|

