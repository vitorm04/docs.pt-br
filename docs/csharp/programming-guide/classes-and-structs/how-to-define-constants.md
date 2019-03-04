---
title: 'Como: Definir constantes em C#'
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, constants
- constants [C#]
ms.assetid: 43f511be-346c-4b8a-995e-aded94542ece
ms.openlocfilehash: a85e7728512922be38658c07314229c26b2461fd
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57201463"
---
# <a name="how-to-define-constants-in-c"></a>Como: Definir constantes em C\#
As constantes são campos cujos valores são definidos em tempo de compilação e nunca podem ser alterados. Use constantes para fornecer nomes significativos em vez de literais numéricos ("números mágicos") a valores especiais.  
  
> [!NOTE]
>  No C#, a diretiva de pré-processador [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) não pode ser utilizada para definir constantes da mesma maneira que é normalmente usada no C e no C++.  
  
 Para definir valores de constantes de tipos integrais (`int`, `byte` e assim por diante), use um tipo enumerado. Para obter mais informações, consulte [enum](../../../csharp/language-reference/keywords/enum.md).  
  
 Para definir constantes não integrais, uma abordagem é agrupá-las em uma única classe estática de nome `Constants`. Isso exigirá que todas as referências às constantes sejam precedidas com o nome de classe, conforme mostrado no exemplo a seguir.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[csProgGuideObjects#89](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#89)]  
  
 O uso do qualificador de nome de classe ajuda a garantir que você e outras pessoas que usam a constante entendam que ele é constante e não pode ser modificado.  
  
## <a name="see-also"></a>Consulte também

- [Classes e Structs](../../../csharp/programming-guide/classes-and-structs/index.md)
