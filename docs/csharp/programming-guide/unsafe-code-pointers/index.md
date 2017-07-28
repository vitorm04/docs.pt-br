---
title: "Código não seguro e ponteiros (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- security [C#], type safety
- C# language, unsafe code
- type safety [C#]
- unsafe keyword [C#]
- unsafe code [C#]
- C# language, pointers
- pointers [C#], about pointers
ms.assetid: b0fcca10-a92d-4f2a-835b-b0ccae6739ee
caps.latest.revision: 24
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 75e11b34f0749270650e0e5b5a2a191a1b9e9f9a
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="unsafe-code-and-pointers-c-programming-guide"></a>Código não seguro e ponteiros (Guia de Programação em C#)
Para manter a segurança de tipos e a segurança, o C# não dá suporte à aritmética de ponteiro por padrão. No entanto, usando a palavra-chave [unsafe](../../../csharp/language-reference/keywords/unsafe.md), você pode definir um contexto não seguro no qual os ponteiros podem ser usados. Para obter mais informações sobre ponteiros, consulte o tópico [Tipos de ponteiro](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md).  
  
> [!NOTE]
>  No CLR (Common Language Runtime), o código não seguro é conhecido como código não verificado. O código não seguro em C# não é necessariamente perigoso. Ele é apenas o código cuja segurança não pode ser verificada pelo CLR. O CLR, portanto, executará somente o código não seguro se ele estiver em um assembly totalmente confiável. Se você usar código não seguro, será sua responsabilidade assegurar que seu código não apresente riscos de segurança ou erros de ponteiro.  
  
## <a name="unsafe-code-overview"></a>Visão Geral de Código Não Seguro  
 O código não seguro tem as propriedades a seguir:  
  
-   Blocos de código, tipos e métodos podem ser definidos como não seguros.  
  
-   Em alguns casos, o código não seguro pode aumentar o desempenho de um aplicativo removendo as verificações de limites de matriz.  
  
-   O código não seguro é necessário quando você chama funções nativas que exigem ponteiros.  
  
-   Usar o código não seguro apresenta riscos de segurança e estabilidade.  
  
-   Para que o C# compile o código não seguro, o aplicativo deve ser compilado com [/unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md).  
  
## <a name="related-sections"></a>Seções relacionadas  
 Para obter mais informações, consulte:  
  
-   [Tipos de ponteiro](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
  
-   [Buffers de tamanho fixo](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md)  
  
-   [Como usar ponteiros para copiar uma matriz de bytes](../../../csharp/programming-guide/unsafe-code-pointers/how-to-use-pointers-to-copy-an-array-of-bytes.md)  
  
-   [unsafe](../../../csharp/language-reference/keywords/unsafe.md)  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)

