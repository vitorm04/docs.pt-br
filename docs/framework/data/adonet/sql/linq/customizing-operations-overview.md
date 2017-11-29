---
title: "Personalizando operações: Visão geral"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a3546296-1443-4b88-aa6e-d41011041ba7
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 7653ca137c93da5174e0ddcd1ced8bdfceaa9edc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="customizing-operations-overview"></a><span data-ttu-id="dff28-102">Personalizando operações: Visão geral</span><span class="sxs-lookup"><span data-stu-id="dff28-102">Customizing Operations: Overview</span></span>
<span data-ttu-id="dff28-103">Por padrão, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] gera SQL dinâmico para inserção, atualização e operações de exclusão com base no mapeamento.</span><span class="sxs-lookup"><span data-stu-id="dff28-103">By default, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generates dynamic SQL for insert, update, and delete operations based on mapping.</span></span> <span data-ttu-id="dff28-104">No entanto, na prática, você geralmente deseja adicionar sua própria lógica de negócios para fornecer segurança, validação e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="dff28-104">However, in practice you typically want to add your own business logic to provide for security, validation, and so forth.</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="dff28-105">técnicas para personalizar essas operações incluem o seguinte.</span><span class="sxs-lookup"><span data-stu-id="dff28-105"> techniques for customizing these operations include the following.</span></span>  
  
## <a name="loading-options"></a><span data-ttu-id="dff28-106">Opções de carregamento</span><span class="sxs-lookup"><span data-stu-id="dff28-106">Loading Options</span></span>  
 <span data-ttu-id="dff28-107">Nas consultas, você pode controlar como os dados relacionados ao seu destino principal são recuperados quando você se conecta ao base de dados.</span><span class="sxs-lookup"><span data-stu-id="dff28-107">In your queries, you can control how much data related to your main target is retrieved when you connect to the database.</span></span> <span data-ttu-id="dff28-108">Essa funcionalidade é implementada amplamente usando <xref:System.Data.Linq.DataLoadOptions>.</span><span class="sxs-lookup"><span data-stu-id="dff28-108">This functionality is implemented largely by using <xref:System.Data.Linq.DataLoadOptions>.</span></span> <span data-ttu-id="dff28-109">Para obter mais informações, consulte [adiado contra Carregando imediata](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).</span><span class="sxs-lookup"><span data-stu-id="dff28-109">For more information, see [Deferred versus Immediate Loading](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).</span></span>  
  
## <a name="partial-methods"></a><span data-ttu-id="dff28-110">Métodos parciais</span><span class="sxs-lookup"><span data-stu-id="dff28-110">Partial Methods</span></span>  
 <span data-ttu-id="dff28-111">No mapeamento padrão, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] fornece métodos parciais para ajudá-lo a implementar a lógica corporativa.</span><span class="sxs-lookup"><span data-stu-id="dff28-111">In its default mapping, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides partial methods to help you implement your business logic.</span></span> <span data-ttu-id="dff28-112">Para obter mais informações, consulte [adicionando negócios lógica por usando métodos parciais](../../../../../../docs/framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md).</span><span class="sxs-lookup"><span data-stu-id="dff28-112">For more information, see [Adding Business Logic By Using Partial Methods](../../../../../../docs/framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md).</span></span>  
  
## <a name="stored-procedures-and-user-defined-functions"></a><span data-ttu-id="dff28-113">Procedimentos e funções definidas pelo usuário armazenados</span><span class="sxs-lookup"><span data-stu-id="dff28-113">Stored Procedures and User-Defined Functions</span></span>  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="dff28-114">oferece suporte ao uso de procedimentos armazenados e funções definidas pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="dff28-114"> supports the use of stored procedures and user-defined functions.</span></span> <span data-ttu-id="dff28-115">Os procedimentos armazenados são usados para personalizar operações.</span><span class="sxs-lookup"><span data-stu-id="dff28-115">Stored procedures are frequently used to customize operations.</span></span> <span data-ttu-id="dff28-116">Para obter mais informações, consulte [Procedimentos armazenados](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="dff28-116">For more information, see [Stored Procedures](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dff28-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dff28-117">See Also</span></span>  
 [<span data-ttu-id="dff28-118">Personalizando a inserção, atualização e exclusão de operações</span><span class="sxs-lookup"><span data-stu-id="dff28-118">Customizing Insert, Update, and Delete Operations</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)
