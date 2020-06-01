---
title: Como usar o guia de programação meu namespace-C#
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, My namespace access
ms.assetid: e7152414-0ea5-4c8e-bf02-c8d5bbe45ff4
ms.openlocfilehash: 268543980ba891b0b30f393ee8982f2863ba9a71
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241936"
---
# <a name="how-to-use-the-my-namespace-c-programming-guide"></a>Como usar o namespace My (guia de programação C#)

O <xref:Microsoft.VisualBasic.MyServices> namespace ( `My` em Visual Basic) fornece acesso fácil e intuitivo a várias classes .net, permitindo que você escreva código que interaja com o computador, o aplicativo, as configurações, os recursos e assim por diante. Embora tenha sido projetado originalmente para ser usado com o Visual Basic, o namespace `MyServices` pode ser usado em aplicativos C#.  
  
 Para obter mais informações sobre como usar o namespace `MyServices` no Visual Basic, consulte [Desenvolvimento com My](../../../visual-basic/developing-apps/development-with-my/index.md).  
  
## <a name="add-a-reference"></a>Adicionar uma referência

 Antes de usar as classes `MyServices` em sua solução, é necessário adicionar uma referência à biblioteca do Visual Basic.  
  
### <a name="add-a-reference-to-the-visual-basic-library"></a>Adicionar uma referência à biblioteca de Visual Basic  
  
1. In **Gerenciador de Soluções**, clique com o botão direito do mouse no nó **Referências** e selecione **Adicionar Referência**.  
  
2. Quando a caixa de diálogo **Referências** for exibida, role a lista para baixo e selecione Microsoft.VisualBasic.dll.  
  
     Também é possível incluir a seguinte linha na seção `using` na inicialização do seu programa.  
  
     [!code-csharp[csProgGuideNamespaces#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#18)]  
  
## <a name="example"></a>Exemplo  
 Este exemplo chama vários métodos estáticos contidos no namespace `MyServices`. Para que esse código seja compilado, deve ser adicionada uma referência ao Microsoft.VisualBasic.DLL ao projeto.  
  
 [!code-csharp[csProgGuideNamespaces#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#19)]  
  
 Nem todas as classes no namespace `MyServices` podem ser chamadas em um aplicativo C#: por exemplo, a classe <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy> não é compatível. Em vez disso, nesse caso específico, podem ser usados os métodos estáticos que fazem parte da <xref:Microsoft.VisualBasic.FileIO.FileSystem>, que também estão contidos na VisualBasic.dll. Por exemplo, veja como usar um desses métodos para duplicar um diretório:  
  
 [!code-csharp[csProgGuideNamespaces#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#20)]  
  
## <a name="see-also"></a>Consulte também

- [Guia de programação C#](../index.md)
- [Namespaces](./index.md)
- [Usando namespaces](./using-namespaces.md)
