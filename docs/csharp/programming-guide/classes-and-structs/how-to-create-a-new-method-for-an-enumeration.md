---
title: Como criar um novo método para uma enumeração (Guia de Programação em C#)
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [C#]
- extension methods [C#], for enums
- enum extensibility [C#]
ms.assetid: 100106f9-1e54-462c-8ebe-3892fe23b6eb
ms.openlocfilehash: 8de44cbddf26af45245709d0e28d2d157256ce59
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33313027"
---
# <a name="how-to-create-a-new-method-for-an-enumeration-c-programming-guide"></a>Como criar um novo método para uma enumeração (Guia de Programação em C#)
Você pode usar métodos de extensão para adicionar funcionalidades específica para um tipo de enumeração específico.  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, a enumeração `Grades` representa as letras possíveis que um aluno pode receber em uma classe. Um método de extensão chamado `Passing` é adicionado ao tipo `Grades` de forma que cada instância desse tipo agora "sabe" se ele representa uma nota de aprovação ou não.  
  
 [!code-csharp[csProgGuideExtensionMethods#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-create-a-new-method-for-an-enumeration_1.cs)]  
  
 Observe que a classe `Extensions` também contém uma variável estática atualizada dinamicamente e que o valor retornado do método de extensão reflete o valor atual dessa variável. Isso demonstra que, nos bastidores, os métodos de extensão são chamados diretamente na classe estática na qual eles são definidos.  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Para executar esse código, copie e cole-o em um projeto de aplicativo de console do Visual C# que foi criado no Visual Studio. Por padrão, esse projeto é direcionado para a versão 3.5 do [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] e ele tem uma referência ao System.Core.dll e uma diretriz `using` para System.Linq. Se um ou mais desses requisitos estiverem ausentes no projeto, você poderá adicioná-los manualmente.  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Métodos de Extensão](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)
