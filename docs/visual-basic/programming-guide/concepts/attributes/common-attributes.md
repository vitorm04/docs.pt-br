---
title: "Atributos comuns (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
ms.assetid: 11fe4894-1bf9-4525-a36b-cddcd3a5d22b
caps.latest.revision: 3
caps.handback.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Atributos comuns (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Este tópico descreve os atributos que são mais comumente usados nos programas em Visual Basic.  
  
-   [Atributos globais](#Global)  
  
-   [Atributo obsoleto](#Obsolete)  
  
-   [Atributo condicional](#Conditional)  
  
-   [Atributos de informações do chamador](#CallerInfo)  
  
-   [Atributos do Visual Basic](#VB)  
  
##  <a name="Global"></a> Atributos globais  
 A maioria dos atributos são aplicados aos elementos de idioma específico, como classes ou métodos; No entanto, alguns atributos são globais — eles se aplicam a um conjunto inteiro ou módulo. Por exemplo, o <xref:System.Reflection.AssemblyVersionAttribute> atributo pode ser usado para incorporar informações de versão em um assembly, como este:  
  
```vb  
<Assembly: AssemblyVersion("1.0.0.0")>  
```  
  
 Atributos globais aparecem no código\-fonte após qualquer nível superior`Imports` instruções e antes de quaisquer declarações de namespace, módulo ou tipo. Atributos globais podem aparecer em vários arquivos de origem, mas os arquivos devem ser criados em uma passagem de compilação única. Para projetos do Visual Basic, os atributos globais geralmente são colocados no arquivo AssemblyInfo VB \(o arquivo é criado automaticamente quando você cria um projeto no Visual Studio\).  
  
 Atributos de assembly são valores que fornecem informações sobre um assembly. Elas se encaixam nas seguintes categorias:  
  
-   Atributos de identidade de assembly  
  
-   Atributos informativos  
  
-   Atributos do manifesto do assembly  
  
### Atributos de identidade de assembly  
 Três atributos \(com um nome forte, se aplicável\) determinam a identidade de um conjunto: nome, versão e cultura. Esses atributos formam o nome completo do assembly e são necessários ao fazer referência a ele no código. Você pode definir a versão e cultura usando atributos de um assembly. No entanto, o valor do nome é definido pelo compilador, a IDE do Visual Studio no [Caixa de diálogo Informações do Assembly](/visual-studio/ide/reference/assembly-information-dialog-box), ou o Assembly Linker \(Al.exe\) quando o assembly é criado, com base em arquivo que contém o manifesto do assembly. O <xref:System.Reflection.AssemblyFlagsAttribute> atributo especifica se várias cópias do conjunto podem coexistir.  
  
 A tabela a seguir mostra os atributos de identidade.  
  
|Atributo|Finalidade|  
|--------------|----------------|  
|<xref:System.Reflection.AssemblyName>|Descreve totalmente a identidade de um assembly.|  
|<xref:System.Reflection.AssemblyVersionAttribute>|Especifica a versão de um assembly.|  
|<xref:System.Reflection.AssemblyCultureAttribute>|Especifica a qual cultura o assembly dá suporte.|  
|<xref:System.Reflection.AssemblyFlagsAttribute>|Especifica se um assembly oferece suporte à execução lado a lado no mesmo computador, no mesmo processo, ou no mesmo domínio do aplicativo.|  
  
### Atributos informativos  
 Você pode usar atributos informativos para fornecer informações de produto para um assembly ou empresas adicionais. A tabela a seguir mostra os atributos informativos definidos no <xref:System.Reflection?displayProperty=fullName> namespace.  
  
|Atributo|Finalidade|  
|--------------|----------------|  
|<xref:System.Reflection.AssemblyProductAttribute>|Define um atributo personalizado que especifica um nome de produto para um manifesto do assembly.|  
|<xref:System.Reflection.AssemblyTrademarkAttribute>|Define um atributo personalizado que especifica uma marca comercial para um manifesto do assembly.|  
|<xref:System.Reflection.AssemblyInformationalVersionAttribute>|Define um atributo personalizado que especifica uma versão informacional para um manifesto do assembly.|  
|<xref:System.Reflection.AssemblyCompanyAttribute>|Define um atributo personalizado que especifica um nome de empresa para um manifesto do assembly.|  
|<xref:System.Reflection.AssemblyCopyrightAttribute>|Define um atributo personalizado que especifica um copyright para um manifesto do assembly.|  
|<xref:System.Reflection.AssemblyFileVersionAttribute>|Instrui o compilador a usar um número de versão específico para o recurso de versão de arquivo do Win32.|  
|<xref:System.CLSCompliantAttribute>|Indica se o assembly é compatível com o Common Language Specification \(CLS\).|  
  
### Atributos do manifesto do assembly  
 Você pode usar atributos do manifesto do assembly para fornecer informações no manifesto do assembly. Isso inclui título, descrição, alias padrão e configuração. A tabela a seguir mostra os atributos de manifesto do assembly definidos no <xref:System.Reflection?displayProperty=fullName> namespace.  
  
|Atributo|Finalidade|  
|--------------|----------------|  
|<xref:System.Reflection.AssemblyTitleAttribute>|Define um atributo personalizado que especifica um título de assembly para um manifesto do assembly.|  
|<xref:System.Reflection.AssemblyDescriptionAttribute>|Define um atributo personalizado que especifica uma descrição de assembly para um manifesto do assembly.|  
|<xref:System.Reflection.AssemblyConfigurationAttribute>|Define um atributo personalizado que especifica uma configuração de assembly \(como comercial ou de depuração\) para um manifesto do assembly.|  
|<xref:System.Reflection.AssemblyDefaultAliasAttribute>|Define um alias amigável padrão para um manifesto do assembly|  
  
##  <a name="Obsolete"></a> Atributo obsoleto  
 O `Obsolete` atributo marca uma entidade programa como um que não é recomendado para uso. Cada uso de uma entidade marcado como obsoleto subsequentemente irá gerar um aviso ou erro, dependendo de como o atributo é configurado. Por exemplo:  
  
```vb  
<System.Obsolete("use class B")>   
Class A  
    Sub Method()  
    End Sub  
End Class  
  
Class B  
    <System.Obsolete("use NewMethod", True)>   
    Sub OldMethod()  
    End Sub  
  
    Sub NewMethod()  
    End Sub  
End Class  
```  
  
 Neste exemplo o `Obsolete` atributo é aplicado à classe `A` e ao método `B.OldMethod`. Como o segundo argumento do construtor de atributo aplicadas a `B.OldMethod` é definido como `true`, esse método causará um erro do compilador, enquanto usando a classe `A` irá produzir apenas um aviso. Chamando `B.NewMethod`, no entanto, não produz nenhum aviso ou erro.  
  
 A cadeia de caracteres fornecida como o primeiro argumento para o construtor de atributo será exibida como parte do aviso ou erro. Por exemplo, quando você usá\-lo com as definições anteriores, o código a seguir gera um erro e dois avisos:  
  
```vb  
' Generates 2 warnings:  
' Dim a As New A  
' Generate no errors or warnings:  
  
Dim b As New B  
b.NewMethod()  
  
' Generates an error, terminating compilation:  
' b.OldMethod()  
```  
  
 Dois avisos para a classe `A` são geradas: uma para a declaração de referência da classe e outra para o construtor da classe.  
  
 O `Obsolete` atributo pode ser usado sem argumentos, mas incluindo uma explicação de por que o item está obsoleto e o que usar em vez disso, é recomendável.  
  
 O `Obsolete` atributo é um atributo de uso único e pode ser aplicado a qualquer entidade que permite que os atributos.`Obsolete` é um alias para <xref:System.ObsoleteAttribute>.  
  
##  <a name="Conditional"></a> Atributo condicional  
 O `Conditional` atributo torna a execução de um método depende de um identificador de pré\-processamento. O `Conditional` é um alias para <xref:System.Diagnostics.ConditionalAttribute>, e pode ser aplicado a um método ou uma classe de atributo.  
  
 Neste exemplo, `Conditional` é aplicado a um método para ativar ou desativar a exibição de informações de diagnóstico específicas do programa:  
  
```vb  
#Const TRACE_ON = True  
Imports System  
Imports System.Diagnostics  
Module TestConditionalAttribute  
    Public Class Trace  
        <Conditional("TRACE_ON")>   
        Public Shared Sub Msg(ByVal msg As String)  
            Console.WriteLine(msg)  
        End Sub  
  
    End Class  
  
    Sub Main()  
        Trace.Msg("Now in Main...")  
        Console.WriteLine("Done.")  
    End Sub  
End Module  
```  
  
 Se o `TRACE_ON` identificador não está definido, nenhuma saída de rastreamento será exibida.  
  
 O `Conditional` atributo é frequentemente usado com o `DEBUG` identificador para habilitar o rastreamento e recursos de log para compilações de depuração, mas não na versão compilações, como esta:  
  
```vb  
<Conditional("DEBUG")>   
Shared Sub DebugMethod()  
  
End Sub  
```  
  
 Quando um método marcado como condicional é chamado, a presença ou ausência do símbolo de pré\-processamento especificado determina se a chamada é incluída ou omitida. Se o símbolo é definido, a chamada será incluída; Caso contrário, a chamada é omitida. Usando `Conditional` é um cartucho de limpeza, alternativa mais elegante e menos propensa a colocar métodos dentro de `#if…#endif` blocos, como este:  
  
```vb  
#If DEBUG Then  
    Sub ConditionalMethod()  
    End Sub  
#End If  
```  
  
 Um método condicional deve ser um método em uma declaração de classe ou estrutura e não deve ter um valor de retorno.  
  
### Usando vários identificadores  
 Se um método com várias `Conditional` atributos, uma chamada para o método é incluída se pelo menos um dos símbolos condicionais é definido \(em outras palavras, os símbolos são logicamente vinculados usando o operador OR\). Neste exemplo, a presença do `A` ou `B` resultará em uma chamada de método:  
  
```vb  
<Conditional("A"), Conditional("B")>   
Shared Sub DoIfAorB()  
  
End Sub  
```  
  
 Para obter o efeito da vinculação logicamente símbolos usando o operador AND, você pode definir métodos condicionais seriais. Por exemplo, o segundo método abaixo será executada somente se ambos os `A` e `B` são definidos:  
  
```vb  
<Conditional("A")>   
Shared Sub DoIfA()  
    DoIfAandB()  
End Sub  
  
<Conditional("B")>   
Shared Sub DoIfAandB()  
    ' Code to execute when both A and B are defined...  
End Sub  
```  
  
### Usar condicional com Classes de atributo  
 O `Conditional` atributo também pode ser aplicado a uma definição de classe de atributo. Neste exemplo, o atributo personalizado `Documentation` apenas adicionará informações de metadados se DEBUG é definido.  
  
```vb  
<Conditional("DEBUG")>   
Public Class Documentation  
    Inherits System.Attribute  
    Private text As String  
    Sub New(ByVal doc_text As String)  
        text = doc_text  
    End Sub  
End Class  
  
Class SampleClass  
    ' This attribute will only be included if DEBUG is defined.  
    <Documentation("This method displays an integer.")>   
    Shared Sub DoWork(ByVal i As Integer)  
        System.Console.WriteLine(i)  
    End Sub  
End Class  
```  
  
##  <a name="CallerInfo"></a> Atributos de informações do chamador  
 Usando atributos de informações do chamador, você pode obter informações sobre o chamador de um método. Você pode obter o caminho do arquivo do código\-fonte, o número da linha no código\-fonte e o nome do membro do chamador.  
  
 Para obter informações do chamador do membro, você deve usar os atributos que são aplicados aos parâmetros opcionais. Cada parâmetro opcional especifica um valor padrão. A tabela a seguir lista os atributos de informações do chamador que são definidos na <xref:System.Runtime.CompilerServices?displayProperty=fullName> namespace:  
  
||||  
|-|-|-|  
|Atributo|Descrição|Tipo|  
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|Caminho completo do arquivo de origem que contém o chamador. Este é o caminho em tempo de compilação.|`String`|  
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|Número da linha no arquivo de origem do qual o método é chamado.|`Integer`|  
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|Nome do método ou o nome da propriedade do chamador. Para obter mais informações, consulte [Informações do chamador \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/caller-information.md).|`String`|  
  
 Para obter mais informações sobre os atributos de informações do chamador, consulte [Informações do chamador \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/caller-information.md).  
  
##  <a name="VB"></a> Atributos do Visual Basic  
 A tabela a seguir lista os atributos que são específicos para o Visual Basic.  
  
|Atributo|Finalidade|  
|--------------|----------------|  
|<xref:Microsoft.VisualBasic.ComClassAttribute>|Indica para o compilador que a classe deve ser exposta como um objeto COM.|  
|<xref:Microsoft.VisualBasic.HideModuleNameAttribute>|Permite que membros de módulo sejam acessados usando somente a qualificação necessária para o módulo.|  
|<xref:Microsoft.VisualBasic.VBFixedStringAttribute>|Especifica o tamanho de uma cadeia de caracteres de comprimento fixo em uma estrutura para uso com o arquivo de entrada e saída funções.|  
|<xref:Microsoft.VisualBasic.VBFixedArrayAttribute>|Especifica o tamanho de uma matriz fixa em uma estrutura para uso com o arquivo de entrada e saída funções.|  
  
### COMClassAttribute  
 Use `COMClassAttribute` para simplificar o processo de criação componentes COM do Visual Basic. Objetos COM são consideravelmente diferentes de assemblies do .NET Framework e sem `COMClassAttribute`, você precisa seguir uma série de etapas para gerar um objeto COM do Visual Basic. Para classes marcadas com `COMClassAttribute`, o compilador executa muitos desses passos automaticamente.  
  
### HideModuleNameAttribute  
 Use `HideModuleNameAttribute` para permitir que membros de módulo sejam acessados usando somente a qualificação necessária para o módulo.  
  
### VBFixedStringAttribute  
 Use `VBFixedStringAttribute` para forçar o Visual Basic para criar uma cadeia de caracteres de comprimento fixo. Cadeias de caracteres são de comprimento variável por padrão, e esse atributo é útil para armazenar cadeias de caracteres em arquivos. O código a seguir demonstra isso:  
  
```vb  
Structure Worker  
    ' The runtime uses VBFixedString to determine   
    ' if the field should be written out as a fixed size.  
    <VBFixedString(10)> Public LastName As String  
    <VBFixedString(7)> Public Title As String  
    <VBFixedString(2)> Public Rank As String  
End Structure  
```  
  
### VBFixedArrayAttribute  
 Use `VBFixedArrayAttribute` para declarar matrizes que foram fixadas em tamanho. Como cadeias de caracteres do Visual Basic, as matrizes são de comprimento variável por padrão. Esse atributo é útil para serialização ou grava dados em arquivos.  
  
## Consulte também  
 <xref:System.Reflection>   
 <xref:System.Attribute>   
 [Guia de programação do Visual Basic](../../../../visual-basic/programming-guide/index.md)   
 [Atributos](../Topic/Extending%20Metadata%20Using%20Attributes.md)   
 [Reflexão \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/reflection.md)   
 [Acessando atributos usando reflexão \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)