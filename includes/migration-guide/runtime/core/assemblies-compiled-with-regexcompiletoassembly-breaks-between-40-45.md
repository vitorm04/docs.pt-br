### <a name="assemblies-compiled-with-regexcompiletoassembly-breaks-between-40-and-45"></a>Assemblies compilados com interrupções Regex.CompileToAssembly entre o 4.0 e o 4.5

|   |   |
|---|---|
|Detalhes|Se uma assembly de expressões regulares compiladas é trabalhada com o .NET Framework 4.5 mas é destinada ao .NET Framework 4, numa tentativa de usar uma das expressões regulares em que a assembly de um sistema com .NET Framework 4 instalado gera uma exceção.|
|Sugestão|Para solucionar esse problema, pode-se seguir uma das seguintes alternativas:<ul><li>Compilar o assembly que contém as expressões regulares com o .NET Framework 4.</li><li>Use uma expressão regular interpretada.</li></ul>|
|Escopo|Secundário|
|Versão|4.5|
|Tipo|Tempo de execução|
|APIs afetadas|<ul><li><xref:System.Text.RegularExpressions.Regex.CompileToAssembly(System.Text.RegularExpressions.RegexCompilationInfo[],System.Reflection.AssemblyName)?displayProperty=nameWithType></li><li><xref:System.Text.RegularExpressions.Regex.CompileToAssembly(System.Text.RegularExpressions.RegexCompilationInfo[],System.Reflection.AssemblyName,System.Reflection.Emit.CustomAttributeBuilder[])?displayProperty=nameWithType></li><li><xref:System.Text.RegularExpressions.Regex.CompileToAssembly(System.Text.RegularExpressions.RegexCompilationInfo[],System.Reflection.AssemblyName,System.Reflection.Emit.CustomAttributeBuilder[],System.String)?displayProperty=nameWithType></li></ul>|

