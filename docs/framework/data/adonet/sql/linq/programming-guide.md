---
title: Guia de Programação
ms.date: 03/30/2017
ms.assetid: ed1012d4-3ff2-4877-af27-93125c4180ea
ms.openlocfilehash: 081b5b9fb0765a69e1f45dd0dc25234b8d217ab4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33361378"
---
# <a name="programming-guide"></a><span data-ttu-id="52ead-102">Guia de Programação</span><span class="sxs-lookup"><span data-stu-id="52ead-102">Programming Guide</span></span>
<span data-ttu-id="52ead-103">Esta seção contém informações sobre como criar e usar o modelo de objeto do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="52ead-103">This section contains information about how to create and use your [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model.</span></span> <span data-ttu-id="52ead-104">Se você estiver usando o Visual Studio, você também pode usar o [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] para executar muitas das mesmas tarefas.</span><span class="sxs-lookup"><span data-stu-id="52ead-104">If you are using Visual Studio, you can also use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to perform many of these same tasks.</span></span>  
  
 <span data-ttu-id="52ead-105">Você também pode pesquisar Microsoft Docs para problemas específicos, e você pode participar de [Fórum do LINQ](http://go.microsoft.com/fwlink/?LinkId=76488), onde você pode abordar tópicos mais complexos detalhadamente com especialistas.</span><span class="sxs-lookup"><span data-stu-id="52ead-105">You can also search Microsoft Docs for specific issues, and you can participate in the [LINQ Forum](http://go.microsoft.com/fwlink/?LinkId=76488), where you can discuss more complex topics in detail with experts.</span></span> <span data-ttu-id="52ead-106">Por fim, o [LINQ to SQL: consulta integrada para dados relacionais](http://go.microsoft.com/fwlink/?LinkId=93205) white paper sobre detalhes [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tecnologia, com exemplos de código do Visual Basic e c#.</span><span class="sxs-lookup"><span data-stu-id="52ead-106">Finally, the [LINQ to SQL: .NET Language-Integrated Query for Relational Data](http://go.microsoft.com/fwlink/?LinkId=93205) white paper details [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technology, complete with Visual Basic and C# code examples.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="52ead-107">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="52ead-107">In This Section</span></span>  
 [<span data-ttu-id="52ead-108">Criando o modelo de objeto</span><span class="sxs-lookup"><span data-stu-id="52ead-108">Creating the Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)  
 <span data-ttu-id="52ead-109">Descreve como gerar um modelo de objeto.</span><span class="sxs-lookup"><span data-stu-id="52ead-109">Describes how to generate an object model.</span></span>  
  
 [<span data-ttu-id="52ead-110">Comunicação com o banco de dados</span><span class="sxs-lookup"><span data-stu-id="52ead-110">Communicating with the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/communicating-with-the-database.md)  
 <span data-ttu-id="52ead-111">Descreve como usar um objeto <xref:System.Data.Linq.DataContext> como um condutor para o banco de dados.</span><span class="sxs-lookup"><span data-stu-id="52ead-111">Describes how to use a <xref:System.Data.Linq.DataContext> object as a conduit to the database.</span></span>  
  
 [<span data-ttu-id="52ead-112">Consultando o banco de dados</span><span class="sxs-lookup"><span data-stu-id="52ead-112">Querying the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)  
 <span data-ttu-id="52ead-113">Descreve como executar consultas no [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] e fornece vários exemplos.</span><span class="sxs-lookup"><span data-stu-id="52ead-113">Describes how to execute queries in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], and provides many examples.</span></span>  
  
 [<span data-ttu-id="52ead-114">Realizando e enviando alterações de dados</span><span class="sxs-lookup"><span data-stu-id="52ead-114">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)  
 <span data-ttu-id="52ead-115">Descreve como alterar dados no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="52ead-115">Describes how change data in the database.</span></span>  
  
 [<span data-ttu-id="52ead-116">Suporte à depuração</span><span class="sxs-lookup"><span data-stu-id="52ead-116">Debugging Support</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/debugging-support.md)  
 <span data-ttu-id="52ead-117">Descreve o suporte disponível para depurar projetos do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="52ead-117">Describes the support available for debugging [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projects.</span></span>  
  
 [<span data-ttu-id="52ead-118">Informações gerais</span><span class="sxs-lookup"><span data-stu-id="52ead-118">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 <span data-ttu-id="52ead-119">Inclui itens adicionais, como a resolução de conflitos de simultaneidade, criando novos bancos de dados e muito mais para usuários mais avançados.</span><span class="sxs-lookup"><span data-stu-id="52ead-119">Includes additional items, such as concurrency conflict resolution, creating new databases, and more, for more advanced users.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="52ead-120">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="52ead-120">Related Sections</span></span>  
 [<span data-ttu-id="52ead-121">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="52ead-121">LINQ to SQL</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/index.md)  
 <span data-ttu-id="52ead-122">Fornece links para tópicos que explicam a tecnologia [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] e demonstram recursos.</span><span class="sxs-lookup"><span data-stu-id="52ead-122">Provides links to topics that explain the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technology and demonstrate features.</span></span>  
  
 [<span data-ttu-id="52ead-123">Procedimentos armazenados</span><span class="sxs-lookup"><span data-stu-id="52ead-123">Stored Procedures</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)  
 <span data-ttu-id="52ead-124">Inclui links para tópicos que ilustram como usar procedimentos armazenados.</span><span class="sxs-lookup"><span data-stu-id="52ead-124">Includes links to topics that illustrate how to use stored procedures.</span></span>  
  
 [<span data-ttu-id="52ead-125">Introdução ao LINQ</span><span class="sxs-lookup"><span data-stu-id="52ead-125">Introduction to LINQ</span></span>](http://msdn.microsoft.com/library/24dddf19-12a0-4707-a4bc-eba4fa7f219e)  
 <span data-ttu-id="52ead-126">Fornece recursos o iniciarão no [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="52ead-126">Provides resources to help you begin to learn about [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>
