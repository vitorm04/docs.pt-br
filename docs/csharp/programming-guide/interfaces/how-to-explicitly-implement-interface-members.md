---
title: Como implementar explicitamente membros de interface – C# guia de programação
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], explicitly implementing
ms.assetid: 514cde76-f981-474e-8b40-9493619f899c
ms.openlocfilehash: dff094aca237ed6146bd9b52813c40549bc99b9b
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77627779"
---
# <a name="how-to-explicitly-implement-interface-members-c-programming-guide"></a>Como implementar explicitamente membros de interface (C# guia de programação)
Este exemplo declara uma [interface](../../language-reference/keywords/interface.md), `IDimensions` e uma classe, `Box`, que implementa explicitamente os membros de interface `GetLength` e `GetWidth`. Os membros são acessados por meio da instância `dimensions` da interface.  
  
## <a name="example"></a>{1&gt;Exemplo&lt;1}  
 [!code-csharp[csProgGuideInheritance#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#8)]  
  
## <a name="robust-programming"></a>Programação Robusta  
  
- Observe que as seguintes linhas, no método `Main`, foram comentadas, pois produziriam erros de compilação. Um membro de interface implementado explicitamente não pode ser acessado de uma instância de [classe](../../language-reference/keywords/class.md):  
  
     [!code-csharp[csProgGuideInheritance#45](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#45)]  
  
- Observe também que as linhas a seguir, no método `Main`, imprimem com êxito as dimensões da caixa, pois os métodos estão sendo chamados de uma instância da interface:  
  
     [!code-csharp[csProgGuideInheritance#46](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#46)]  
  
## <a name="see-also"></a>Consulte também

- [Guia de Programação em C#](../index.md)
- [Classes e Structs](../classes-and-structs/index.md)
- [Interfaces](./index.md)
- [Como implementar explicitamente membros de duas interfaces](./how-to-explicitly-implement-members-of-two-interfaces.md)
