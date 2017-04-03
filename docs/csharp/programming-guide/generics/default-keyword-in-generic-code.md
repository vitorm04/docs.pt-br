---
title: "Palavra-chave default em código genérico (Guia de programação em C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- generics [C#], default keyword
- default keyword [C#], generic programming
ms.assetid: b9daf449-4e64-496e-8592-6ed2c8875a98
caps.latest.revision: 22
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 17591eb07d2bf8af0e13c62b632df29e00b45df6
ms.lasthandoff: 03/13/2017

---
# <a name="default-keyword-in-generic-code-c-programming-guide"></a>Palavra-chave default em código genérico (Guia de Programação em C#)
Um problema que surge em métodos e classes genéricas é como atribuir um valor padrão a um tipo parametrizado T quando você não souber, com antecedência, o seguinte:  
  
-   Se T será um tipo de referência ou um tipo de valor.  
  
-   Se T for um tipo de valor, ele será um valor numérico ou um struct.  
  
 Dada uma variável t de um tipo parametrizado T, a instrução t = null só será válida se T for um tipo de referência e t = 0 funcionará somente para tipos de valor numérico, mas não para structs. A solução é usar a palavra-chave `default`, que retornará null para tipos de referência e zero para tipos de valor numérico. Para structs, ela retornará cada membro do struct inicializado como zero ou null, dependendo se forem tipos de valor ou de referência. Para tipos que permitem valor nulo, o padrão retorna um <xref:System.Nullable%601?displayProperty=fullName>, que é inicializado como qualquer struct.  
  
 O exemplo a seguir da classe `GenericList<T>` mostra como usar a palavra-chave `default`. Para obter mais informações, consulte [Visão geral de genéricos](../../../csharp/programming-guide/generics/introduction-to-generics.md).  
  
 [!code-cs[csProgGuideGenerics#41](../../../csharp/programming-guide/generics/codesnippet/CSharp/default-keyword-in-generic-code_1.cs)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Collections.Generic>   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Genéricos](../../../csharp/programming-guide/generics/index.md)   
 [Métodos Genéricos](../../../csharp/programming-guide/generics/generic-methods.md)   
 [Genéricos](https://msdn.microsoft.com/library/ms172192)
