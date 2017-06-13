---
title: "Como inicializar um dicionário com um inicializador de coleção (Guia de programação em C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- collection initializers [C#], with Dictionary
ms.assetid: 25283922-f8ee-40dc-a639-fac30804ec71
caps.latest.revision: 10
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 31905a37f09db5f5192123f0118252fbe8b02eff
ms.openlocfilehash: 6c6f15772f098618d63a48ada122b1e98ef5e62d
ms.contentlocale: pt-br
ms.lasthandoff: 06/12/2017

---
# <a name="how-to-initialize-a-dictionary-with-a-collection-initializer-c-programming-guide"></a>Como inicializar um dicionário com um inicializador de coleção (Guia de Programação em C#)
Um método <xref:System.Collections.Generic.Dictionary`2> contains a collection of key/value pairs. Its <xref:System.Collections.Generic.Dictionary`2.Add*> utiliza dois parâmetros, um para a chave e um para o valor. Para inicializar um método <xref:System.Collections.Generic.Dictionary`2>, or any collection whose `Add`, use vários parâmetros, coloque cada conjunto de parâmetros entre chaves conforme mostrado no exemplo a seguir.  
  
## <a name="example"></a>Exemplo  
 No exemplo de código a seguir, um <xref:System.Collections.Generic.Dictionary`2> is initialized with instances of type `StudentName`.  
  
 [!code-cs[csProgGuideLINQ#34](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-a-dictionary-with-a-collection-initializer_1.cs)]  
  
 Observe os dois pares de chaves em cada elemento da coleção. As chaves internas coloque o inicializador de objeto para o `StudentName`, e as chaves mais externas coloque o inicializador para o par chave/valor que será adicionado ao `students` <xref:System.Collections.Generic.Dictionary`2>. Por fim, todo o inicializador de coleção do dicionário é colocado entre chaves.  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Para executar esse código, copie e cole a classe em um projeto de aplicativo de console do Visual C# que foi criado no [!INCLUDE[vs_current_short](~/includes/vs-current-short-md.md)]. Por padrão, esse projeto é direcionado à versão 3.5 do [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] e tem uma referência a System.Core.dll e uma diretriz de uso para System.Linq. Se um ou mais desses requisitos estiverem ausentes no projeto, você poderá adicioná-los manualmente.   
  
## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Inicializadores de objeto e coleção](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)
