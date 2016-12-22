---
title: "Atributos (Visual Basic) | Microsoft Docs"
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
ms.assetid: 1449f69b-c063-41de-8d89-f0bbdcf96ac6
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Atributos (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Atributos fornecem um método poderoso de associar metadados ou informações declarativas, código \(assemblies, tipos, métodos, propriedades e assim por diante\). Depois que um atributo está associado uma entidade de programa, o atributo pode ser consultado em tempo de execução usando uma técnica chamada *reflexão*. Para obter mais informações, consulte [Reflexão \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/reflection.md).  
  
 Atributos têm as seguintes propriedades:  
  
-   Atributos adicionar metadados ao seu programa.*Metadados* informações sobre os tipos definidos em um programa. Todos os assemblies .NET contêm um conjunto de metadados que descrevem os tipos e membros de tipo definidos no assembly especificado. Você pode adicionar atributos personalizados para especificar qualquer informação adicional é necessária. Para obter mais informações, consulte, [Criando atributos personalizados \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md).  
  
-   Você pode aplicar um ou mais atributos todos assemblies, módulos ou elementos pequenos programas como classes e propriedades.  
  
-   Atributos podem aceitar argumentos da mesma forma como métodos e propriedades.  
  
-   Seu programa pode examinar seus próprios metadados ou os metadados em outros programas por meio de reflexão. Para obter mais informações, consulte [Acessando atributos usando reflexão \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).  
  
## Usando atributos  
 Atributos podem ser colocados em qualquer declaração, embora um atributo específico pode restringir os tipos de declarações no qual ele é válido. No Visual Basic, um atributo está entre colchetes angulares \(\<\>\). Ele deverá aparecer imediatamente antes do elemento ao qual ela é aplicada, na mesma linha.  
  
 Neste exemplo, o <xref:System.SerializableAttribute> atributo é usado para aplicar uma característica específica a uma classe:  
  
```vb  
<System.Serializable()> Public Class SampleClass  
    ' Objects of this type can be serialized.  
End Class  
```  
  
 Um método com o atributo <xref:System.Runtime.InteropServices.DllImportAttribute> é declarado como este:  
  
```vb  
Imports System.Runtime.InteropServices  
```  
  
```vb  
<System.Runtime.InteropServices.DllImport("user32.dll")>   
Sub SampleMethod()  
End Sub  
```  
  
 Mais de um atributo pode ser colocado em uma declaração:  
  
```vb  
Imports System.Runtime.InteropServices  
```  
  
```vb  
Sub MethodA(<[In](), Out()> ByVal x As Double)  
End Sub  
Sub MethodB(<Out(), [In]()> ByVal x As Double)  
End Sub  
```  
  
 Alguns atributos podem ser especificados mais de uma vez para uma determinada entidade. É um exemplo de tal um atributo multiuse <xref:System.Diagnostics.ConditionalAttribute>:  
  
```vb  
<Conditional("DEBUG"), Conditional("TEST1")>   
Sub TraceMethod()  
End Sub  
```  
  
> [!NOTE]
>  Por convenção, todos os nomes de atributo terminam com a palavra "Atributo" para distingui\-los de outros itens no .NET Framework. No entanto, você não precisa especificar o sufixo de atributo quando usando atributos no código. Por exemplo, `[DllImport]` é equivalente a `[DllImportAttribute]`, mas `DllImportAttribute` é o nome do atributo real no .NET Framework.  
  
### Parâmetros de atributo  
 Muitos atributos têm parâmetros, que podem ser nomeada, sem nome ou posição. Quaisquer parâmetros posicionais devem ser especificados em uma determinada ordem e não podem ser omitidos; parâmetros nomeados são opcionais e podem ser especificados em qualquer ordem. Parâmetros posicionais são especificados pela primeira vez. Por exemplo, esses três atributos são equivalentes:  
  
```vb  
<DllImport("user32.dll")>  
<DllImport("user32.dll", SetLastError:=False, ExactSpelling:=False)>  
<DllImport("user32.dll", ExactSpelling:=False, SetLastError:=False)>  
```  
  
 O nome da DLL, o primeiro parâmetro é posicional e sempre vem em primeiro lugar; os outros são nomeados. Nesse caso, nomeados padrão de parâmetros como false, portanto elas podem ser omitidas. Consulte a documentação do atributo individuais para obter informações sobre valores de parâmetro padrão.  
  
### Destinos de Atributos  
 O *destino* de um atributo é a entidade à qual o atributo se aplica. Por exemplo, um atributo pode aplicar a uma classe, um método específico ou um assembly inteiro. Por padrão, um atributo aplica\-se ao elemento que ela precede. Mas você pode explicitamente identificar, por exemplo, se um atributo é aplicado a um método, ou seu parâmetro ou seu valor de retorno.  
  
 Para identificar explicitamente um atributo de destino, use a seguinte sintaxe:  
  
```vb  
<target : attribute-list>  
```  
  
 A lista de possíveis `target` valores é mostrado na tabela a seguir.  
  
|Valor de destino|Aplica\-se a|  
|----------------------|------------------|  
|`assembly`|Assembly inteiro|  
|`module`|Módulo de assembly atual \(que é diferente de um módulo do Visual Basic\)|  
  
 O exemplo a seguir mostra como aplicar atributos a módulos e assemblies. Para obter mais informações, consulte [Atributos comuns \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/attributes/common-attributes.md).  
  
```vb  
Imports System.Reflection  
<Assembly: AssemblyTitleAttribute("Production assembly 4"),   
Module: CLSCompliant(True)>   
```  
  
## Usos comuns para os atributos  
 A lista a seguir inclui alguns dos usos comuns de atributos no código:  
  
-   Marcar métodos usando o `WebMethod` atributo nos serviços da Web para indicar que o método deve ser chamado por meio do protocolo SOAP. Para obter mais informações, consulte <xref:System.Web.Services.WebMethodAttribute>.  
  
-   Que descreve como realizar marshaling de parâmetros de método ao interoperar com código nativo. Para obter mais informações, consulte <xref:System.Runtime.InteropServices.MarshalAsAttribute>.  
  
-   Descrever as propriedades COM classes, métodos e interfaces.  
  
-   Chamada não gerenciada no código usando o <xref:System.Runtime.InteropServices.DllImportAttribute> classe.  
  
-   Descrevendo o assembly em termos de versão, título, descrição ou marca comercial.  
  
-   Descrever quais membros de uma classe para serializar para persistência.  
  
-   Que descreve como mapear entre nós XML para serialização de XML e membros de classe.  
  
-   Descrever os requisitos de segurança para métodos.  
  
-   Especificando as características usado para impor a segurança.  
  
-   Controlando otimizações pelo compilador just\-in\-time \(JIT\) para que o código permaneça fácil de depurar.  
  
-   Obtendo informações sobre o chamador de um método.  
  
## Seções relacionadas  
 Para obter mais informações, consulte:  
  
-   [Criando atributos personalizados \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)  
  
-   [Acessando atributos usando reflexão \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)  
  
-   [Como: criar uma união C\/C\+\+ usando atributos \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/attributes/how-to-create-a-c-cpp-union-by-using-attributes.md)  
  
-   [Atributos comuns \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/attributes/common-attributes.md)  
  
-   [Informações do chamador \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/caller-information.md)  
  
## Consulte também  
 [Guia de programação do Visual Basic](../../../../visual-basic/programming-guide/index.md)   
 [Reflexão \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/reflection.md)   
 [Atributos](../Topic/Extending%20Metadata%20Using%20Attributes.md)