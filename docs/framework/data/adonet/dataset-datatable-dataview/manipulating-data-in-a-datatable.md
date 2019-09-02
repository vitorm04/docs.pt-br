---
title: Manipulando dados em uma DataTable
ms.date: 03/30/2017
ms.assetid: 5cb86d48-a987-4af4-80e0-8cc2c8373d62
ms.openlocfilehash: 83b1a4b6c0e477ac918a2bb4e454718fc58ece0b
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203498"
---
# <a name="manipulating-data-in-a-datatable"></a><span data-ttu-id="a12ae-102">Manipulando dados em uma DataTable</span><span class="sxs-lookup"><span data-stu-id="a12ae-102">Manipulating Data in a DataTable</span></span>
<span data-ttu-id="a12ae-103">Após criar i, <xref:System.Data.DataTable> em um <xref:System.Data.DataSet>, você pode executar as mesmas atividades que faria ao usar uma tabela em um banco de dados.</span><span class="sxs-lookup"><span data-stu-id="a12ae-103">After creating a <xref:System.Data.DataTable> in a <xref:System.Data.DataSet>, you can perform the same activities that you would when using a table in a database.</span></span> <span data-ttu-id="a12ae-104">Você pode adicionar, exibir, editar e excluir dados na tabela; você pode monitorar erros e eventos; e pode consultar os dados na tabela.</span><span class="sxs-lookup"><span data-stu-id="a12ae-104">You can add, view, edit, and delete data in the table; you can monitor errors and events; and you can query the data in the table.</span></span> <span data-ttu-id="a12ae-105">Ao modificar dados em uma **DataTable**, você também pode verificar se as alterações são precisas e determinar se as alterações devem ser aceitas ou rejeitadas programaticamente.</span><span class="sxs-lookup"><span data-stu-id="a12ae-105">When modifying data in a **DataTable**, you can also verify whether the changes are accurate, and determine whether to programmatically accept or reject the changes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a12ae-106">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="a12ae-106">In This Section</span></span>  
 [<span data-ttu-id="a12ae-107">Adicionando dados a um DataTable</span><span class="sxs-lookup"><span data-stu-id="a12ae-107">Adding Data to a DataTable</span></span>](adding-data-to-a-datatable.md)  
 <span data-ttu-id="a12ae-108">Explica como criar novas linhas e adicioná-las a uma tabela.</span><span class="sxs-lookup"><span data-stu-id="a12ae-108">Explains how to create new rows and add them to a table.</span></span>  
  
 [<span data-ttu-id="a12ae-109">Exibindo dados em uma DataTable</span><span class="sxs-lookup"><span data-stu-id="a12ae-109">Viewing Data in a DataTable</span></span>](viewing-data-in-a-datatable.md)  
 <span data-ttu-id="a12ae-110">Descreve como acessar os dados em uma linha, incluindo as versões originais e atuais dos dados.</span><span class="sxs-lookup"><span data-stu-id="a12ae-110">Describes how to access the data in a row, including original and current versions of the data.</span></span>  
  
 [<span data-ttu-id="a12ae-111">O método Load</span><span class="sxs-lookup"><span data-stu-id="a12ae-111">The Load Method</span></span>](the-load-method.md)  
 <span data-ttu-id="a12ae-112">Descreve o uso do método **Load** para preencher uma **DataTable** com linhas.</span><span class="sxs-lookup"><span data-stu-id="a12ae-112">Describes the use of the **Load** method to fill a **DataTable** with rows.</span></span>  
  
 [<span data-ttu-id="a12ae-113">Edições de DataTable</span><span class="sxs-lookup"><span data-stu-id="a12ae-113">DataTable Edits</span></span>](datatable-edits.md)  
 <span data-ttu-id="a12ae-114">Explica como alterar os dados em uma linha, incluindo suspensão das alterações em uma linha até que as alterações propostas sejam verificadas e aceitas.</span><span class="sxs-lookup"><span data-stu-id="a12ae-114">Explains how to modify the data in a row, including suspending the changes to a row until the proposed changes are verified and accepted.</span></span>  
  
 [<span data-ttu-id="a12ae-115">Estados e versões de linha</span><span class="sxs-lookup"><span data-stu-id="a12ae-115">Row States and Row Versions</span></span>](row-states-and-row-versions.md)  
 <span data-ttu-id="a12ae-116">Fornece informações sobre os estados diferentes de uma linha.</span><span class="sxs-lookup"><span data-stu-id="a12ae-116">Provides information about the different states of a row.</span></span>  
  
 [<span data-ttu-id="a12ae-117">Exclusão de DataRow</span><span class="sxs-lookup"><span data-stu-id="a12ae-117">DataRow Deletion</span></span>](datarow-deletion.md)  
 <span data-ttu-id="a12ae-118">Descreve como remover uma linha de uma tabela.</span><span class="sxs-lookup"><span data-stu-id="a12ae-118">Describes how to remove a row from a table.</span></span>  
  
 [<span data-ttu-id="a12ae-119">Informações de erro de linha</span><span class="sxs-lookup"><span data-stu-id="a12ae-119">Row Error Information</span></span>](row-error-information.md)  
 <span data-ttu-id="a12ae-120">Explica como inserir informações de erro por linha, para ajudar a resolver problemas com os dados em um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a12ae-120">Explains how to insert error information per row, to help resolve problems with the data within an application.</span></span>  
  
 [<span data-ttu-id="a12ae-121">AcceptChanges e RejectChanges</span><span class="sxs-lookup"><span data-stu-id="a12ae-121">AcceptChanges and RejectChanges</span></span>](acceptchanges-and-rejectchanges.md)  
 <span data-ttu-id="a12ae-122">Explica como aceitar ou rejeitar alterações feitas em uma linha.</span><span class="sxs-lookup"><span data-stu-id="a12ae-122">Explains how to accept or reject the changes made to a row.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a12ae-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a12ae-123">See also</span></span>

- [<span data-ttu-id="a12ae-124">DataTables</span><span class="sxs-lookup"><span data-stu-id="a12ae-124">DataTables</span></span>](datatables.md)
- [<span data-ttu-id="a12ae-125">Manipulação de eventos de DataTable</span><span class="sxs-lookup"><span data-stu-id="a12ae-125">Handling DataTable Events</span></span>](handling-datatable-events.md)
- <span data-ttu-id="a12ae-126">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="a12ae-126">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
