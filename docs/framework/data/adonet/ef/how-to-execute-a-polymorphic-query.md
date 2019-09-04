---
title: 'Como: executar uma consulta polimorfo'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2f05da1e-845b-4f14-83e4-c6353a850553
ms.openlocfilehash: 49e0a6b44af0729959fabf6278cc6d8ecf37a16b
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251506"
---
# <a name="how-to-execute-a-polymorphic-query"></a><span data-ttu-id="adf86-102">Como: executar uma consulta polimorfo</span><span class="sxs-lookup"><span data-stu-id="adf86-102">How to: Execute a Polymorphic Query</span></span>

<span data-ttu-id="adf86-103">Este tópico mostra como executar uma [!INCLUDE[esql](../../../../../includes/esql-md.md)] consulta polimórfica usando o operador [OfType](./language-reference/oftype-entity-sql.md) .</span><span class="sxs-lookup"><span data-stu-id="adf86-103">This topic shows how to execute a polymorphic [!INCLUDE[esql](../../../../../includes/esql-md.md)] query using the [OFTYPE](./language-reference/oftype-entity-sql.md) operator.</span></span>

### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="adf86-104">Para executar o código nesse exemplo</span><span class="sxs-lookup"><span data-stu-id="adf86-104">To run the code in this example</span></span>

1. <span data-ttu-id="adf86-105">Adicione o [modelo escolar](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)) ao seu projeto e configure seu projeto para usar o Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="adf86-105">Add the [School Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)) to your project and configure your project to use the Entity Framework.</span></span> <span data-ttu-id="adf86-106">Para obter mais informações, confira [Como: Use o assistente](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))de modelo de dados de entidade.</span><span class="sxs-lookup"><span data-stu-id="adf86-106">For more information, see [How to: Use the Entity Data Model Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>

2. <span data-ttu-id="adf86-107">Na página de código do seu aplicativo, adicione as seguintes instruções `using` (`Imports` no Visual Basic):</span><span class="sxs-lookup"><span data-stu-id="adf86-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>

    [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
    [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]

3. <span data-ttu-id="adf86-108">Modifique o modelo conceitual para ter uma herança de tabela por hierarquia seguindo as etapas descritas [em Walkthrough: Mapeamento de herança – tabela por hierarquia](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716683(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="adf86-108">Modify the conceptual model to have a table-per-hierarchy inheritance by following the steps in [Walkthrough: Mapping Inheritance - Table-per-Hierarchy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716683(v=vs.100)).</span></span>

## <a name="example"></a><span data-ttu-id="adf86-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="adf86-109">Example</span></span>

<span data-ttu-id="adf86-110">O seguinte exemplo usa um operador de OFTYPE para obter e exibir uma coleção somente de `OnsiteCourses` de uma coleção de `Courses`.</span><span class="sxs-lookup"><span data-stu-id="adf86-110">The following example uses an OFTYPE operator to get and display a collection of only `OnsiteCourses` from a collection of `Courses`.</span></span>

[!code-csharp[DP EntityServices Concepts#PolymorphicQuery](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#polymorphicquery)]
[!code-vb[DP EntityServices Concepts#PolymorphicQuery](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#polymorphicquery)]

## <a name="see-also"></a><span data-ttu-id="adf86-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="adf86-111">See also</span></span>

- [<span data-ttu-id="adf86-112">Provedor EntityClient para Entity Framework</span><span class="sxs-lookup"><span data-stu-id="adf86-112">EntityClient Provider for the Entity Framework</span></span>](entityclient-provider-for-the-entity-framework.md)
- <span data-ttu-id="adf86-113">[Entity SQL Language](./language-reference/entity-sql-language.md) (Linguagem SQL de entidade)</span><span class="sxs-lookup"><span data-stu-id="adf86-113">[Entity SQL Language](./language-reference/entity-sql-language.md)</span></span>
