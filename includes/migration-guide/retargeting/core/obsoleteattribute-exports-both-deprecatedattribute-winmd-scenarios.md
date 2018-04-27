### <a name="obsoleteattribute-exports-as-both-obsoleteattribute-and-deprecatedattribute-in-winmd-scenarios"></a>ObsoleteAttribute exporta ObsoleteAttribute e DeprecatedAttribute em cenários WinMD

|   |   |
|---|---|
|Detalhes|Quando você cria uma biblioteca de Metadados do Windows (arquivo .winmd), o atributo <xref:System.ObsoleteAttribute?displayProperty=name> é exportado como <xref:System.ObsoleteAttribute?displayProperty=name> e [ Windows.Foundation.DeprecatedAttribute](https://docs.microsoft.com/uwp/api/windows.foundation.metadata.deprecatedattribute).|
|Sugestão|A recompilação do código-fonte existente que usa o atributo <xref:System.ObsoleteAttribute?displayProperty=name> pode gerar avisos durante o consumo desse código do C++/CX ou JavaScript. Não é recomendável aplicar <xref:System.ObsoleteAttribute?displayProperty=name> e [Windows.Foundation.DeprecatedAttribute](https://docs.microsoft.com/uwp/api/windows.foundation.metadata.deprecatedattribute) ao código em assemblies gerenciados, isso pode gerar avisos de compilação.|
|Escopo|Microsoft Edge|
|Versão|4.5.1|
|Tipo|Redirecionando|

