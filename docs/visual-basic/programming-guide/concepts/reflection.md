---
title: "Reflexão (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
ms.assetid: d991bc0f-d16a-4ac5-9351-70e5c5b9891b
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 3ae042933575849e105d7b681634a61319c1d6ee
ms.lasthandoff: 03/13/2017

---
# <a name="reflection-visual-basic"></a>Reflexão (Visual Basic)
Reflexão fornece objetos (do tipo <xref:System.Type>) que descrevem os assemblies, módulos e tipos.</xref:System.Type> Você pode usar reflexão dinamicamente criar uma instância de um tipo, o tipo de associação a um objeto existente, ou obter o tipo de um objeto existente e chamar seus métodos ou acessar suas propriedades e campos. Se você estiver usando atributos no seu código, reflexão permite acessá-los. Para obter mais informações, consulte [atributos](https://msdn.microsoft.com/library/5x6cd29c).  
  
 Aqui está um exemplo simples de reflexão usando o método estático `GetType` - herdadas por todos os tipos do `Object` base class - para obter o tipo de uma variável:  
  
```vb  
' Using GetType to obtain type information:  
Dim i As Integer = 42  
Dim type As System.Type = i.GetType()  
System.Console.WriteLine(type)  
```  
  
 A saída é:  
  
 `System.Int32`  
  
 O exemplo a seguir usa a reflexão para obter o nome completo do assembly carregado.  
  
```vb  
' Using Reflection to get information from an Assembly:  
Dim info As System.Reflection.Assembly = GetType(System.Int32).Assembly  
System.Console.WriteLine(info)  
```  
  
 A saída é:  
  
 `mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
## <a name="reflection-overview"></a>Visão geral de reflexão  
 A reflexão é útil nas seguintes situações:  
  
-   Quando você tem que acessar atributos nos metadados do seu programa. Para obter mais informações, consulte [Recuperando informações armazenadas em atributos](http://msdn.microsoft.com/library/37dfe4e3-7da0-48b6-a3d9-398981524e1c).  
  
-   Para examinar e instanciar tipos em um assembly.  
  
-   Para criar novos tipos em tempo de execução. Usar as classes em <xref:System.Reflection.Emit>.</xref:System.Reflection.Emit>  
  
-   Para executar ligação tardia, acessar métodos em tipos criados em tempo de execução. Consulte o tópico [Carregando dinamicamente e usando tipos](http://msdn.microsoft.com/library/db985bec-5942-40ec-b13a-771ae98623dc).  
  
## <a name="related-sections"></a>Seções relacionadas  
 Para saber mais:  
  
-   [Reflexão](http://msdn.microsoft.com/library/d1a58e7f-fb39-4d50-bf84-e3b8f9bf9775)  
  
-   [Exibindo informações de tipo](http://msdn.microsoft.com/library/7e7303a9-4064-4738-b4e7-b75974ed70d2)  
  
-   [Reflexão e tipos genéricos](http://msdn.microsoft.com/library/f7180fc5-dd41-42d4-8a8e-1b34288e06de)  
  
-   <xref:System.Reflection.Emit></xref:System.Reflection.Emit>  
  
-   [Recuperando informações armazenadas em atributos](http://msdn.microsoft.com/library/37dfe4e3-7da0-48b6-a3d9-398981524e1c)  
  
## <a name="see-also"></a>Consulte também  
 [Guia de programação em Visual Basic](../../../visual-basic/programming-guide/index.md)   
 [Assemblies no Common Language Runtime](https://msdn.microsoft.com/library/k3677y81)
