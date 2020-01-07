---
title: Como implementar explicitamente membros de interface – C# guia de programação
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], explicitly implementing
ms.assetid: 514cde76-f981-474e-8b40-9493619f899c
ms.openlocfilehash: 4efc325b3587ee790cce739727506a28c3a1f524
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635399"
---
# <a name="how-to-explicitly-implement-interface-members-c-programming-guide"></a>Como implementar explicitamente membros de interface (C# guia de programação)
Este exemplo declara uma [interface](../../language-reference/keywords/interface.md), `IDimensions` e uma classe, `Box`, que implementa explicitamente os membros de interface `getLength` e `getWidth`. Os membros são acessados por meio da instância `dimensions` da interface.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[csProgGuideInheritance#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#8)]  
  
## <a name="robust-programming"></a>Programação Robusta  
  
- Observe que as seguintes linhas, no método `Main`, foram comentadas, pois produziriam erros de compilação. Um membro de interface implementado explicitamente não pode ser acessado de uma instância de [classe](../../language-reference/keywords/class.md):  
  
     [!code-csharp[csProgGuideInheritance#45](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#45)]  
  
- Observe também que as linhas a seguir, no método `Main`, imprimem com êxito as dimensões da caixa, pois os métodos estão sendo chamados de uma instância da interface:  
  
     [!code-csharp[csProgGuideInheritance#46](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#46)]  
  
## <a name="see-also"></a>Veja também

- [Guia de Programação em C#](../index.md)
- [Classes e Structs](../classes-and-structs/index.md)
- [Interfaces](./index.md)
- [Como implementar explicitamente membros de duas interfaces](./how-to-explicitly-implement-members-of-two-interfaces.md)
