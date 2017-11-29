---
title: "Guia de Programação"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ed1012d4-3ff2-4877-af27-93125c4180ea
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 03d4febc7e61425d0057c48949b18281ca3dec4b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="programming-guide"></a><span data-ttu-id="d8457-102">Guia de Programação</span><span class="sxs-lookup"><span data-stu-id="d8457-102">Programming Guide</span></span>
<span data-ttu-id="d8457-103">Esta seção contém informações sobre como criar e usar o modelo de objeto do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d8457-103">This section contains information about how to create and use your [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model.</span></span> <span data-ttu-id="d8457-104">Se você estiver usando o [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)], também poderá usar o [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] para executar muitas dessas mesmas tarefas.</span><span class="sxs-lookup"><span data-stu-id="d8457-104">If you are using [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)], you can also use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to perform many of these same tasks.</span></span>  
  
 <span data-ttu-id="d8457-105">Você também pode pesquisar Microsoft Docs para problemas específicos, e você pode participar de [Fórum do LINQ](http://go.microsoft.com/fwlink/?LinkId=76488), onde você pode abordar tópicos mais complexos detalhadamente com especialistas.</span><span class="sxs-lookup"><span data-stu-id="d8457-105">You can also search Microsoft Docs for specific issues, and you can participate in the [LINQ Forum](http://go.microsoft.com/fwlink/?LinkId=76488), where you can discuss more complex topics in detail with experts.</span></span> <span data-ttu-id="d8457-106">Por fim, o white paper [LINQ to SQL: .NET Language-Integrated Query for Relational Data](http://go.microsoft.com/fwlink/?LinkId=93205) (LINQ to SQL: consulta integrada à linguagem do .NET para dados relacionais) fornece informações detalhadas sobre a tecnologia [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], com exemplos de código C# e do [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d8457-106">Finally, the [LINQ to SQL: .NET Language-Integrated Query for Relational Data](http://go.microsoft.com/fwlink/?LinkId=93205) white paper details [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technology, complete with [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] and C# code examples.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d8457-107">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="d8457-107">In This Section</span></span>  
 [<span data-ttu-id="d8457-108">Criando o modelo de objeto</span><span class="sxs-lookup"><span data-stu-id="d8457-108">Creating the Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)  
 <span data-ttu-id="d8457-109">Descreve como gerar um modelo de objeto.</span><span class="sxs-lookup"><span data-stu-id="d8457-109">Describes how to generate an object model.</span></span>  
  
 [<span data-ttu-id="d8457-110">Comunicação com o banco de dados</span><span class="sxs-lookup"><span data-stu-id="d8457-110">Communicating with the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/communicating-with-the-database.md)  
 <span data-ttu-id="d8457-111">Descreve como usar um objeto <xref:System.Data.Linq.DataContext> como um condutor para o banco de dados.</span><span class="sxs-lookup"><span data-stu-id="d8457-111">Describes how to use a <xref:System.Data.Linq.DataContext> object as a conduit to the database.</span></span>  
  
 [<span data-ttu-id="d8457-112">Consultando o banco de dados</span><span class="sxs-lookup"><span data-stu-id="d8457-112">Querying the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)  
 <span data-ttu-id="d8457-113">Descreve como executar consultas no [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] e fornece vários exemplos.</span><span class="sxs-lookup"><span data-stu-id="d8457-113">Describes how to execute queries in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], and provides many examples.</span></span>  
  
 [<span data-ttu-id="d8457-114">Fazendo e enviando alterações de dados</span><span class="sxs-lookup"><span data-stu-id="d8457-114">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)  
 <span data-ttu-id="d8457-115">Descreve como alterar dados no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="d8457-115">Describes how change data in the database.</span></span>  
  
 [<span data-ttu-id="d8457-116">Suporte à depuração</span><span class="sxs-lookup"><span data-stu-id="d8457-116">Debugging Support</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/debugging-support.md)  
 <span data-ttu-id="d8457-117">Descreve o suporte disponível para depurar projetos do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d8457-117">Describes the support available for debugging [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projects.</span></span>  
  
 [<span data-ttu-id="d8457-118">Informações de plano de fundo</span><span class="sxs-lookup"><span data-stu-id="d8457-118">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 <span data-ttu-id="d8457-119">Inclui itens adicionais, como a resolução de conflitos de simultaneidade, criando novos bancos de dados e muito mais para usuários mais avançados.</span><span class="sxs-lookup"><span data-stu-id="d8457-119">Includes additional items, such as concurrency conflict resolution, creating new databases, and more, for more advanced users.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d8457-120">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="d8457-120">Related Sections</span></span>  
 [<span data-ttu-id="d8457-121">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="d8457-121">LINQ to SQL</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/index.md)  
 <span data-ttu-id="d8457-122">Fornece links para tópicos que explicam a tecnologia [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] e demonstram recursos.</span><span class="sxs-lookup"><span data-stu-id="d8457-122">Provides links to topics that explain the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technology and demonstrate features.</span></span>  
  
 [<span data-ttu-id="d8457-123">Procedimentos armazenados</span><span class="sxs-lookup"><span data-stu-id="d8457-123">Stored Procedures</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)  
 <span data-ttu-id="d8457-124">Inclui links para tópicos que ilustram como usar procedimentos armazenados.</span><span class="sxs-lookup"><span data-stu-id="d8457-124">Includes links to topics that illustrate how to use stored procedures.</span></span>  
  
 [<span data-ttu-id="d8457-125">Introdução ao LINQ</span><span class="sxs-lookup"><span data-stu-id="d8457-125">Introduction to LINQ</span></span>](http://msdn.microsoft.com/library/24dddf19-12a0-4707-a4bc-eba4fa7f219e)  
 <span data-ttu-id="d8457-126">Fornece recursos o iniciarão no [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d8457-126">Provides resources to help you begin to learn about [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>
