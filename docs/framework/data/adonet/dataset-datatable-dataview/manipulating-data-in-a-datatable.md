---
title: Manipulando dados em uma DataTable
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5cb86d48-a987-4af4-80e0-8cc2c8373d62
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 58d04a3ba1d73d4236353ff4f08a747ac7b6f0cc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="manipulating-data-in-a-datatable"></a><span data-ttu-id="8a9d7-102">Manipulando dados em uma DataTable</span><span class="sxs-lookup"><span data-stu-id="8a9d7-102">Manipulating Data in a DataTable</span></span>
<span data-ttu-id="8a9d7-103">Após criar i, <xref:System.Data.DataTable> em um <xref:System.Data.DataSet>, você pode executar as mesmas atividades que faria ao usar uma tabela em um banco de dados.</span><span class="sxs-lookup"><span data-stu-id="8a9d7-103">After creating a <xref:System.Data.DataTable> in a <xref:System.Data.DataSet>, you can perform the same activities that you would when using a table in a database.</span></span> <span data-ttu-id="8a9d7-104">Você pode adicionar, exibir, editar e excluir dados na tabela; você pode monitorar erros e eventos; e pode consultar os dados na tabela.</span><span class="sxs-lookup"><span data-stu-id="8a9d7-104">You can add, view, edit, and delete data in the table; you can monitor errors and events; and you can query the data in the table.</span></span> <span data-ttu-id="8a9d7-105">Ao modificar dados em um **DataTable**, você também pode verificar se as alterações são precisas e determinam se deseja aceitar ou rejeitar as alterações de programaticamente.</span><span class="sxs-lookup"><span data-stu-id="8a9d7-105">When modifying data in a **DataTable**, you can also verify whether the changes are accurate, and determine whether to programmatically accept or reject the changes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8a9d7-106">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="8a9d7-106">In This Section</span></span>  
 [<span data-ttu-id="8a9d7-107">Adicionando dados a um DataTable</span><span class="sxs-lookup"><span data-stu-id="8a9d7-107">Adding Data to a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-data-to-a-datatable.md)  
 <span data-ttu-id="8a9d7-108">Explica como criar novas linhas e adicioná-las a uma tabela.</span><span class="sxs-lookup"><span data-stu-id="8a9d7-108">Explains how to create new rows and add them to a table.</span></span>  
  
 [<span data-ttu-id="8a9d7-109">Exibindo dados em uma DataTable</span><span class="sxs-lookup"><span data-stu-id="8a9d7-109">Viewing Data in a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/viewing-data-in-a-datatable.md)  
 <span data-ttu-id="8a9d7-110">Descreve como acessar os dados em uma linha, incluindo as versões originais e atuais dos dados.</span><span class="sxs-lookup"><span data-stu-id="8a9d7-110">Describes how to access the data in a row, including original and current versions of the data.</span></span>  
  
 [<span data-ttu-id="8a9d7-111">O método Load</span><span class="sxs-lookup"><span data-stu-id="8a9d7-111">The Load Method</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/the-load-method.md)  
 <span data-ttu-id="8a9d7-112">Descreve o uso do **carga** método para preencher um **DataTable** com linhas.</span><span class="sxs-lookup"><span data-stu-id="8a9d7-112">Describes the use of the **Load** method to fill a **DataTable** with rows.</span></span>  
  
 [<span data-ttu-id="8a9d7-113">Edições de DataTable</span><span class="sxs-lookup"><span data-stu-id="8a9d7-113">DataTable Edits</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-edits.md)  
 <span data-ttu-id="8a9d7-114">Explica como alterar os dados em uma linha, incluindo suspensão das alterações em uma linha até que as alterações propostas sejam verificadas e aceitas.</span><span class="sxs-lookup"><span data-stu-id="8a9d7-114">Explains how to modify the data in a row, including suspending the changes to a row until the proposed changes are verified and accepted.</span></span>  
  
 [<span data-ttu-id="8a9d7-115">Estados e versões de linha</span><span class="sxs-lookup"><span data-stu-id="8a9d7-115">Row States and Row Versions</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)  
 <span data-ttu-id="8a9d7-116">Fornece informações sobre os estados diferentes de uma linha.</span><span class="sxs-lookup"><span data-stu-id="8a9d7-116">Provides information about the different states of a row.</span></span>  
  
 [<span data-ttu-id="8a9d7-117">Exclusão de DataRow</span><span class="sxs-lookup"><span data-stu-id="8a9d7-117">DataRow Deletion</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datarow-deletion.md)  
 <span data-ttu-id="8a9d7-118">Descreve como remover uma linha de uma tabela.</span><span class="sxs-lookup"><span data-stu-id="8a9d7-118">Describes how to remove a row from a table.</span></span>  
  
 [<span data-ttu-id="8a9d7-119">Informações de erro de linha</span><span class="sxs-lookup"><span data-stu-id="8a9d7-119">Row Error Information</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-error-information.md)  
 <span data-ttu-id="8a9d7-120">Explica como inserir informações de erro por linha, para ajudar a resolver problemas com os dados em um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8a9d7-120">Explains how to insert error information per row, to help resolve problems with the data within an application.</span></span>  
  
 [<span data-ttu-id="8a9d7-121">AcceptChanges e RejectChanges</span><span class="sxs-lookup"><span data-stu-id="8a9d7-121">AcceptChanges and RejectChanges</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/acceptchanges-and-rejectchanges.md)  
 <span data-ttu-id="8a9d7-122">Explica como aceitar ou rejeitar alterações feitas em uma linha.</span><span class="sxs-lookup"><span data-stu-id="8a9d7-122">Explains how to accept or reject the changes made to a row.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a9d7-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8a9d7-123">See Also</span></span>  
 [<span data-ttu-id="8a9d7-124">DataTables</span><span class="sxs-lookup"><span data-stu-id="8a9d7-124">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [<span data-ttu-id="8a9d7-125">Manipulação de eventos de DataTable</span><span class="sxs-lookup"><span data-stu-id="8a9d7-125">Handling DataTable Events</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md)  
 <span data-ttu-id="8a9d7-126">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="8a9d7-126">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
