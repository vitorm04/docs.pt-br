### <a name="encoderparameter-ctor-is-obsolete"></a>O construtor EncoderParameter está obsoleto

|   |   |
|---|---|
|Detalhes|O construtor <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)> agora está obsoleto e introduzirá novos avisos de compilação se for usado.|
|Sugestão|Embora o construtor <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)> continue funcionando, o seguinte construtor deverá ser usado no lugar para evitar o aviso de compilação obsoleta durante a recompilação de código com as ferramentas do .NET 4.5: <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Drawing.Imaging.EncoderParameterValueType,System.IntPtr)>.|
|Escopo|Secundário|
|Versão|4.5|
|Tipo|Redirecionando|
|APIs afetadas|<ul><li><xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)?displayProperty=nameWithType></li></ul>|

