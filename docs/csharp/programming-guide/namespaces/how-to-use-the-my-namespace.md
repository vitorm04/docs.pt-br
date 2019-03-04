---
title: 'Como: usar o My Namespace – Guia de Programação em C#'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, My namespace access
ms.assetid: e7152414-0ea5-4c8e-bf02-c8d5bbe45ff4
ms.openlocfilehash: b56a421dd7b34bf006e1e6609bbb8ecc5f56e0bf
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56971254"
---
# <a name="how-to-use-the-my-namespace-c-programming-guide"></a>Como: usar o My Namespace (Guia de Programação em C#)
O namespace <xref:Microsoft.VisualBasic.MyServices> (`My` no Visual Basic) oferece acesso rápido e intuitivo a inúmeras classes do .NET Framework, permitindo que você grave um código que interaja com o computador, com o aplicativo, com as configurações, com os recursos e assim por diante. Embora tenha sido projetado originalmente para ser usado com o Visual Basic, o namespace `MyServices` pode ser usado em aplicativos C#.  
  
 Para obter mais informações sobre como usar o namespace `MyServices` no Visual Basic, consulte [Desenvolvimento com My](../../../visual-basic/developing-apps/development-with-my/index.md).  
  
## <a name="adding-a-reference"></a>Adicionando uma referência  
 Antes de usar as classes `MyServices` em sua solução, é necessário adicionar uma referência à biblioteca do Visual Basic.  
  
#### <a name="to-add-a-reference-to-the-visual-basic-library"></a>Para adicionar uma referência à biblioteca do Visual Basic  
  
1.  In **Gerenciador de Soluções**, clique com o botão direito do mouse no nó **Referências** e selecione **Adicionar Referência**.  
  
2.  Quando a caixa de diálogo **Referências** for exibida, role a lista para baixo e selecione Microsoft.VisualBasic.dll.  
  
     Também é possível incluir a seguinte linha na seção `using` na inicialização do seu programa.  
  
     [!code-csharp[csProgGuideNamespaces#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#18)]  
  
## <a name="example"></a>Exemplo  
 Este exemplo chama vários métodos estáticos contidos no namespace `MyServices`. Para que esse código seja compilado, deve ser adicionada uma referência ao Microsoft.VisualBasic.DLL ao projeto.  
  
 [!code-csharp[csProgGuideNamespaces#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#19)]  
  
 Nem todas as classes no namespace `MyServices` podem ser chamadas em um aplicativo C#: por exemplo, a classe <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy> não é compatível. Em vez disso, nesse caso específico, podem ser usados os métodos estáticos que fazem parte da <xref:Microsoft.VisualBasic.FileIO.FileSystem>, que também estão contidos na VisualBasic.dll. Por exemplo, veja como usar um desses métodos para duplicar um diretório:  
  
 [!code-csharp[csProgGuideNamespaces#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#20)]  
  
## <a name="see-also"></a>Consulte também

- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)
- [Namespaces](../../../csharp/programming-guide/namespaces/index.md)
- [Usando namespaces](../../../csharp/programming-guide/namespaces/using-namespaces.md)
