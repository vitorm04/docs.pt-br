### <a name="machinekeyencode-and-machinekeydecode-methods-are-now-obsolete"></a>Os métodos MachineKey.Encode e MachineKey.Decode agora estão obsoletos

|   |   |
|---|---|
|Detalhes|Esses métodos são agora obsoletos. A compilação de código que chama estes métodos gera um aviso do compilador.|
|Sugestão|As alternativas recomendadas são <xref:System.Web.Security.MachineKey.Protect(System.Byte[],System.String[])> e <xref:System.Web.Security.MachineKey.Unprotect(System.Byte[],System.String[])>. Como alternativa, os avisos de compilação podem ser suprimidos ou evitados usando um compilador mais antigo. Ainda há suporte para as APIs.|
|Escopo|Secundário|
|Versão|4.5|
|Tipo|Redirecionando|
|APIs afetadas|<ul><li><xref:System.Web.Security.MachineKey.Encode(System.Byte[],System.Web.Security.MachineKeyProtection)?displayProperty=nameWithType></li><li><xref:System.Web.Security.MachineKey.Decode(System.String,System.Web.Security.MachineKeyProtection)?displayProperty=nameWithType></li></ul>|

