---
title: "Atributos (c#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
ms.assetid: f148f13f-a0d5-4f22-9c87-4b73d5dde270
caps.latest.revision: 3
caps.handback.revision: 3
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Atributos (c#)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Atributos fornecem um método poderoso de associar metadados ou informações declarativas, código \(assemblies, tipos, métodos, propriedades e assim por diante\). Depois que um atributo está associado uma entidade de programa, o atributo pode ser consultado em tempo de execução usando uma técnica chamada *reflexão*. Para obter mais informações, consulte [Reflexão \(c\#\)](../../../../csharp/programming-guide/concepts/reflection.md).  
  
 Atributos têm as seguintes propriedades:  
  
-   Atributos adicionar metadados ao seu programa.*Metadados* informações sobre os tipos definidos em um programa. Todos os assemblies .NET contêm um conjunto de metadados que descrevem os tipos e membros de tipo definidos no assembly especificado. Você pode adicionar atributos personalizados para especificar qualquer informação adicional é necessária. Para obter mais informações, consulte, [Criando atributos personalizados \(c\#\)](../../../../csharp/programming-guide/concepts/attributes/creating-custom-attributes.md).  
  
-   Você pode aplicar um ou mais atributos todos assemblies, módulos ou elementos pequenos programas como classes e propriedades.  
  
-   Atributos podem aceitar argumentos da mesma forma como métodos e propriedades.  
  
-   Seu programa pode examinar seus próprios metadados ou os metadados em outros programas por meio de reflexão. Para obter mais informações, consulte [Acessando atributos usando reflexão \(c\#\)](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).  
  
## Usando atributos  
 Atributos podem ser colocados em qualquer declaração, embora um atributo específico pode restringir os tipos de declarações no qual ele é válido. No c\#, você especificar um atributo colocando o nome do atributo, entre colchetes \(\[\]\), acima da declaração da entidade à qual se aplica.  
  
 Neste exemplo, o <xref:System.SerializableAttribute> atributo é usado para aplicar uma característica específica a uma classe:  
  
```c#  
[System.Serializable]  
public class SampleClass  
{  
    // Objects of this type can be serialized.  
}  
```  
  
 Um método com o atributo <xref:System.Runtime.InteropServices.DllImportAttribute> é declarado como este:  
  
```c#  
using System.Runtime.InteropServices;  
```  
  
```c#  
[System.Runtime.InteropServices.DllImport("user32.dll")]  
extern static void SampleMethod();  
```  
  
 Mais de um atributo pode ser colocado em uma declaração:  
  
```c#  
using System.Runtime.InteropServices;  
```  
  
```c#  
void MethodA([In][Out] ref double x) { }  
void MethodB([Out][In] ref double x) { }  
void MethodC([In, Out] ref double x) { }  
```  
  
 Alguns atributos podem ser especificados mais de uma vez para uma determinada entidade. É um exemplo de tal um atributo multiuse <xref:System.Diagnostics.ConditionalAttribute>:  
  
```c#  
[Conditional("DEBUG"), Conditional("TEST1")]  
void TraceMethod()  
{  
    // ...  
}  
```  
  
> [!NOTE]
>  Por convenção, todos os nomes de atributo terminam com a palavra "Atributo" para distingui\-los de outros itens no .NET Framework. No entanto, você não precisa especificar o sufixo de atributo quando usando atributos no código. Por exemplo, `[DllImport]` é equivalente a `[DllImportAttribute]`, mas `DllImportAttribute` é o nome do atributo real no .NET Framework.  
  
### Parâmetros de atributo  
 Muitos atributos têm parâmetros, que podem ser nomeada, sem nome ou posição. Quaisquer parâmetros posicionais devem ser especificados em uma determinada ordem e não podem ser omitidos; parâmetros nomeados são opcionais e podem ser especificados em qualquer ordem. Parâmetros posicionais são especificados pela primeira vez. Por exemplo, esses três atributos são equivalentes:  
  
```c#  
[DllImport("user32.dll")]  
[DllImport("user32.dll", SetLastError=false, ExactSpelling=false)]  
[DllImport("user32.dll", ExactSpelling=false, SetLastError=false)]  
```  
  
 O nome da DLL, o primeiro parâmetro é posicional e sempre vem em primeiro lugar; os outros são nomeados. Nesse caso, nomeados padrão de parâmetros como false, portanto elas podem ser omitidas. Consulte a documentação do atributo individuais para obter informações sobre valores de parâmetro padrão.  
  
### Destinos de Atributos  
 O *destino* de um atributo é a entidade à qual o atributo se aplica. Por exemplo, um atributo pode aplicar a uma classe, um método específico ou um assembly inteiro. Por padrão, um atributo aplica\-se ao elemento que ela precede. Mas você pode explicitamente identificar, por exemplo, se um atributo é aplicado a um método, ou seu parâmetro ou seu valor de retorno.  
  
 Para identificar explicitamente um atributo de destino, use a seguinte sintaxe:  
  
```c#  
[target : attribute-list]  
```  
  
 A lista de possíveis `target` valores é mostrado na tabela a seguir.  
  
|Valor de destino|Aplica\-se a|  
|----------------------|------------------|  
|`assembly`|Assembly inteiro|  
|`module`|Módulo do assembly atual|  
|`field`|Campo em uma classe ou uma estrutura|  
|`event`|Evento|  
|`method`|Método ou `get` e `set` acessadores de propriedade|  
|`param`|Parâmetros de método ou `set` parâmetros de acessador de propriedade|  
|`property`|Propriedade|  
|`return`|Valor de retorno de um método, indexador de propriedade, ou `get` acessador de propriedade|  
|`type`|Estrutura, classe, interface, enum ou delegate|  
  
 O exemplo a seguir mostra como aplicar atributos a módulos e assemblies. Para obter mais informações, consulte [Atributos comuns \(c\#\)](../../../../csharp/programming-guide/concepts/attributes/common-attributes.md).  
  
```c#  
using System;  
using System.Reflection;  
[assembly: AssemblyTitleAttribute("Production assembly 4")]  
[module: CLSCompliant(true)]  
```  
  
 O exemplo a seguir mostra como aplicar atributos a métodos, parâmetros de método e valores de retorno de método em c\#.  
  
```c#  
// default: applies to method  
[SomeAttr]  
int Method1() { return 0; }  
  
// applies to method  
[method: SomeAttr]  
int Method2() { return 0; }  
  
// applies to return value  
[return: SomeAttr]  
int Method3() { return 0; }  
```  
  
> [!NOTE]
>  Independentemente de destinos no qual `SomeAttr` é definido para ser válido, o `return` destino deve ser especificado, mesmo se `SomeAttr` foram definidas para aplicar somente para valores de retorno. Em outras palavras, o compilador não usará `AttributeUsage` informações para resolver os destinos de atributos ambíguo. Para obter mais informações, consulte [AttributeUsage \(c\#\)](../../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md).  
  
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
  
-   [Criando atributos personalizados \(c\#\)](../../../../csharp/programming-guide/concepts/attributes/creating-custom-attributes.md)  
  
-   [Acessando atributos usando reflexão \(c\#\)](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)  
  
-   [Como: criar uma união C\/C\+\+ usando atributos \(c\#\)](../../../../csharp/programming-guide/concepts/attributes/how-to-create-a-c-cpp-union-by-using-attributes.md)  
  
-   [Atributos comuns \(c\#\)](../../../../csharp/programming-guide/concepts/attributes/common-attributes.md)  
  
-   [Informações do chamador \(c\#\)](../../../../visual-basic/programming-guide/concepts/caller-information.md)  
  
## Consulte também  
 [Guia de Programação em C\#](../../../../csharp/programming-guide/index.md)   
 [Reflexão \(c\#\)](../../../../csharp/programming-guide/concepts/reflection.md)   
 [Atributos](../Topic/Extending%20Metadata%20Using%20Attributes.md)