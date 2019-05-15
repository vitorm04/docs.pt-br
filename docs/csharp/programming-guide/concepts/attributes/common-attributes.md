---
title: Atributos comuns (C#)
ms.date: 07/20/2015
ms.assetid: 785a0526-6c0e-4599-8c61-ccdc88dd9965
ms.openlocfilehash: bb06fc72fc336df257c6b674d3eaa4fa47801da0
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64603331"
---
# <a name="common-attributes-c"></a>Atributos comuns (C#)
Este tópico descreve os atributos que são mais comumente usados nos programas em C#.  
  
- [Atributos globais](#Global)  
  
- [Atributo obsoleto](#Obsolete)  
  
- [Atributo condicional](#Conditional)  
  
- [Atributos de informações do chamador](#CallerInfo)  
  
## <a name="Global"></a> Atributos globais  
 A maioria dos atributos são aplicados aos elementos específicos de linguagem, como classes ou métodos. No entanto, alguns atributos são globais. Eles se aplicam a um assembly inteiro ou módulo. Por exemplo, o atributo <xref:System.Reflection.AssemblyVersionAttribute> pode ser usado para inserir informações de versão em um assembly, desta maneira:  
  
```csharp  
[assembly: AssemblyVersion("1.0.0.0")]  
```  
  
 Os atributos globais aparecem no código-fonte depois de qualquer diretiva `using` de nível superior e antes de qualquer declaração de namespace, módulo ou tipo. Os atributos globais podem aparecer em vários arquivos de origem, mas os arquivos devem ser compilados em uma única passagem de compilação. Em projetos do C#, os atributos globais são colocados no arquivo AssemblyInfo.cs.  
  
 Os atributos de assembly são valores que fornecem informações sobre um assembly. Eles se enquadram nas seguintes categorias:  
  
- Atributos de identidade do assembly  
  
- Atributos informativos  
  
- Atributos de manifesto do assembly  
  
### <a name="assembly-identity-attributes"></a>Atributos de Identidade do Assembly  
 Três atributos (com um nome forte, se aplicável) determinam a identidade de um assembly: nome, versão e cultura. Esses atributos formam o nome completo do assembly e são necessários ao fazer referência a ele no código. Você pode definir a versão e a cultura de um assembly, usando atributos. No entanto, o valor do nome é definido pelo compilador, pelo IDE do Visual Studio na [caixa de diálogo de Informações do Assembly](/visualstudio/ide/reference/assembly-information-dialog-box) ou pelo Assembly Linker (Al.exe) quando o assembly é criado, com base no arquivo que contém o manifesto do assembly. O atributo <xref:System.Reflection.AssemblyFlagsAttribute> especifica se várias cópias do assembly podem coexistir.  
  
 A tabela a seguir mostra os atributos de identidade.  
  
|Atributo|Finalidade|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyName>|Descreve completamente a identidade de um assembly.|  
|<xref:System.Reflection.AssemblyVersionAttribute>|Especifica a versão de um assembly.|  
|<xref:System.Reflection.AssemblyCultureAttribute>|Especifica a qual cultura o assembly dá suporte.|  
|<xref:System.Reflection.AssemblyFlagsAttribute>|Especifica se um assembly dá suporte à execução lado a lado no mesmo computador, no mesmo processo ou no mesmo domínio do aplicativo.|  
  
### <a name="informational-attributes"></a>Atributos Informativos  
 Você pode usar atributos informativos para fornecer informações adicionais corporativas ou de produto para um assembly. A tabela a seguir mostra os atributos informativos definidos no namespace <xref:System.Reflection?displayProperty=nameWithType>.  
  
|Atributo|Finalidade|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyProductAttribute>|Define um atributo personalizado que especifica um nome de produto para um manifesto do assembly.|  
|<xref:System.Reflection.AssemblyTrademarkAttribute>|Define um atributo personalizado que especifica uma marca registrada para um manifesto do assembly.|  
|<xref:System.Reflection.AssemblyInformationalVersionAttribute>|Define um atributo personalizado que especifica uma versão informativa para um manifesto do assembly.|  
|<xref:System.Reflection.AssemblyCompanyAttribute>|Define um atributo personalizado que especifica um nome de empresa para um manifesto do assembly.|  
|<xref:System.Reflection.AssemblyCopyrightAttribute>|Define um atributo personalizado que especifica os direitos autorais para um manifesto do assembly.|  
|<xref:System.Reflection.AssemblyFileVersionAttribute>|Instrui o compilador a usar um número de versão específico para o recurso de versão de arquivo do Win32.|  
|<xref:System.CLSCompliantAttribute>|Indica se o assembly está em conformidade com a CLS (Common Language Specification).|  
  
### <a name="assembly-manifest-attributes"></a>Atributos de Manifesto do Assembly  
 Você pode usar atributos de manifesto do assembly para fornecer informações no manifesto do assembly. Isso inclui título, descrição, alias padrão e configuração. A tabela a seguir mostra os atributos de manifesto do assembly definidos no namespace <xref:System.Reflection?displayProperty=nameWithType>.  
  
|Atributo|Finalidade|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyTitleAttribute>|Define um atributo personalizado que especifica um título de assembly para um manifesto do assembly.|  
|<xref:System.Reflection.AssemblyDescriptionAttribute>|Define um atributo personalizado que especifica uma descrição de assembly para um manifesto do assembly.|  
|<xref:System.Reflection.AssemblyConfigurationAttribute>|Define um atributo personalizado que especifica uma configuração de assembly (como comercial ou de depuração) para um manifesto do assembly. assembly.|  
|<xref:System.Reflection.AssemblyDefaultAliasAttribute>|Define um alias amigável padrão para um manifesto do assembly|  
  
## <a name="Obsolete"></a> Atributo obsoleto  
 O atributo `Obsolete` marca uma entidade programa como não recomendada para uso. Cada uso de uma entidade marcada como obsoleta gerará subsequentemente um aviso ou erro, dependendo de como o atributo é configurado. Por exemplo:  
  
```csharp  
[System.Obsolete("use class B")]  
class A  
{  
    public void Method() { }  
}  
class B  
{  
    [System.Obsolete("use NewMethod", true)]  
    public void OldMethod() { }  
    public void NewMethod() { }  
}  
```  
  
 Neste exemplo o atributo `Obsolete` é aplicado à classe `A` e ao método `B.OldMethod`. Como o segundo argumento do construtor de atributo aplicado a `B.OldMethod` está definido como `true`, esse método causará um erro do compilador, enquanto que ao usar a classe `A`, produzirá apenas um aviso. Chamar `B.NewMethod`, no entanto, não produz aviso nem erro.  
  
 A cadeia de caracteres fornecida como o primeiro argumento para o construtor de atributo será exibida como parte do aviso ou erro. Por exemplo, ao usá-lo com as definições anteriores, o código a seguir gera um erro e dois avisos:  
  
```csharp  
// Generates 2 warnings:  
// A a = new A();  
  
// Generate no errors or warnings:  
B b = new B();  
b.NewMethod();  
  
// Generates an error, terminating compilation:  
// b.OldMethod();  
```  
  
 São gerados dois avisos para a classe `A`: um para a declaração da referência de classe e outro para o construtor de classe.  
  
 O atributo `Obsolete` pode ser usado sem argumentos, mas é recomendável incluir uma explicação de por que o item está obsoleto e o que deve ser usado no lugar dele.  
  
 O atributo `Obsolete` é um atributo de uso único e pode ser aplicado a qualquer entidade que permite atributos. `Obsolete` é um alias para <xref:System.ObsoleteAttribute>.  
  
## <a name="Conditional"></a> Atributo condicional  
 O atributo `Conditional` torna a execução de um método dependente de um identificador de pré-processamento. O atributo `Conditional` é um alias para <xref:System.Diagnostics.ConditionalAttribute> e pode ser aplicado a um método ou uma classe de atributo.  
  
 Neste exemplo, `Conditional` é aplicado a um método para habilitar ou desabilitar a exibição de informações de diagnóstico específicas do programa:  
  
```csharp  
#define TRACE_ON  
using System;  
using System.Diagnostics;  
  
public class Trace  
{  
    [Conditional("TRACE_ON")]  
    public static void Msg(string msg)  
    {  
        Console.WriteLine(msg);  
    }  
}  
  
public class ProgramClass  
{  
    static void Main()  
    {  
        Trace.Msg("Now in Main...");  
        Console.WriteLine("Done.");  
    }  
}  
```  
  
 Se o identificador `TRACE_ON` não estiver definido, nenhuma saída de rastreamento será exibida.  
  
 O atributo `Conditional` é frequentemente usado com o identificador `DEBUG` para habilitar recursos de rastreamento e de registro em log para builds de depuração, mas não em builds de versão, dessa maneira:  
  
```csharp  
[Conditional("DEBUG")]  
static void DebugMethod()  
{  
}  
```  
  
 Quando um método marcado como condicional é chamado, a presença ou ausência do símbolo de pré-processamento especificado determina se a chamada será incluída ou omitida. Se o símbolo estiver definido, a chamada será incluída, caso contrário, a chamada será omitida. O uso de `Conditional` é uma alternativa mais limpa, mais elegante e menos propensa a erros para incluir métodos dentro de blocos `#if…#endif`, dessa maneira:  
  
```csharp  
#if DEBUG  
    void ConditionalMethod()  
    {  
    }  
#endif  
```  
  
 Um método condicional deve ser um método em uma declaração de classe ou de struct e não deve ter um valor retornado.  
  
### <a name="using-multiple-identifiers"></a>Usando vários identificadores  
 Se um método tem vários atributos `Conditional`, uma chamada para o método será incluída se pelo menos um dos símbolos condicionais for definido (em outras palavras, os símbolos são logicamente vinculados através do uso do operador OR). Neste exemplo, a presença de `A` ou `B` resultará em uma chamada de método:  
  
```csharp  
[Conditional("A"), Conditional("B")]  
static void DoIfAorB()  
{  
    // ...  
}  
```  
  
 Para alcançar o efeito da vinculação lógica de símbolos usando o operador AND, você pode definir métodos condicionais em série. Por exemplo, o segundo método abaixo será executado somente se `A` e `B` estiverem definidos:  
  
```csharp
[Conditional("A")]  
static void DoIfA()  
{  
    DoIfAandB();  
}  
  
[Conditional("B")]  
static void DoIfAandB()  
{  
    // Code to execute when both A and B are defined...  
}  
```  
  
### <a name="using-conditional-with-attribute-classes"></a>Usando condicional com classes de atributos  
 O atributo `Conditional` também pode ser aplicado a uma definição de classe de atributos. Neste exemplo, o atributo personalizado `Documentation` só adicionará informações aos metadados se DEBUG estiver definido.  
  
```csharp  
[Conditional("DEBUG")]  
public class Documentation : System.Attribute  
{  
    string text;  
  
    public Documentation(string text)  
    {  
        this.text = text;  
    }  
}  
  
class SampleClass  
{  
    // This attribute will only be included if DEBUG is defined.  
    [Documentation("This method displays an integer.")]  
    static void DoWork(int i)  
    {  
        System.Console.WriteLine(i.ToString());  
    }  
}  
```  
  
## <a name="CallerInfo"></a> Atributos de informações do chamador  
 Ao usar atributos de informações do chamador, você pode obter informações sobre o chamador de um método. Você pode obter o caminho do arquivo do código-fonte, o número de linha no código-fonte e o nome do membro do chamador.  
  
 Para obter informações do chamador do membro, você usa os atributos que são aplicados aos parâmetros opcionais. Cada parâmetro opcional especifica um valor padrão. A tabela a seguir lista os atributos de informações do chamador que são definidos no namespace de <xref:System.Runtime.CompilerServices?displayProperty=nameWithType>:  
  
|Atributo|Descrição|Tipo|  
|---|---|---|  
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|O caminho completo do arquivo de origem que contém o chamador. Esse é o caminho em tempo de compilação.|`String`|  
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|Número de linha no arquivo de origem do qual o método é chamado.|`Integer`|  
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|Nome do método ou nome da propriedade do chamador. Para obter mais informações, consulte [Informações do chamador (C#)](../../../../csharp/programming-guide/concepts/caller-information.md).|`String`|  
  
 Para obter mais informações sobre os atributos de informações do chamador, consulte [Informações do chamador (C#)](../../../../csharp/programming-guide/concepts/caller-information.md).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Reflection>
- <xref:System.Attribute>
- [Guia de Programação em C#](../../../../csharp/programming-guide/index.md)
- [Atributos](../../../../../docs/standard/attributes/index.md)
- [Reflexão (C#)](../../../../csharp/programming-guide/concepts/reflection.md)
- [Acessando atributos usando reflexão (C#)](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
