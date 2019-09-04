---
title: 'Personalizar operações: Visão geral'
ms.date: 03/30/2017
ms.assetid: a3546296-1443-4b88-aa6e-d41011041ba7
ms.openlocfilehash: 48116887471709c60c9666f68c7ebdd0e6d128a1
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70247526"
---
# <a name="customizing-operations-overview"></a><span data-ttu-id="deab9-102">Personalizar operações: Visão geral</span><span class="sxs-lookup"><span data-stu-id="deab9-102">Customizing Operations: Overview</span></span>
<span data-ttu-id="deab9-103">Por padrão, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] o gera SQL dinâmico para operações de inserção, atualização e exclusão com base no mapeamento.</span><span class="sxs-lookup"><span data-stu-id="deab9-103">By default, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generates dynamic SQL for insert, update, and delete operations based on mapping.</span></span> <span data-ttu-id="deab9-104">No entanto, na prática, normalmente você desejará adicionar sua própria lógica de negócios para fornecer segurança, validação e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="deab9-104">However, in practice you typically want to add your own business logic to provide for security, validation, and so forth.</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="deab9-105">as técnicas para personalizar essas operações incluem o seguinte.</span><span class="sxs-lookup"><span data-stu-id="deab9-105">techniques for customizing these operations include the following.</span></span>  
  
## <a name="loading-options"></a><span data-ttu-id="deab9-106">Opções de carregamento</span><span class="sxs-lookup"><span data-stu-id="deab9-106">Loading Options</span></span>  
 <span data-ttu-id="deab9-107">Nas consultas, você pode controlar como os dados relacionados ao seu destino principal são recuperados quando você se conecta ao base de dados.</span><span class="sxs-lookup"><span data-stu-id="deab9-107">In your queries, you can control how much data related to your main target is retrieved when you connect to the database.</span></span> <span data-ttu-id="deab9-108">Essa funcionalidade é implementada amplamente usando <xref:System.Data.Linq.DataLoadOptions>.</span><span class="sxs-lookup"><span data-stu-id="deab9-108">This functionality is implemented largely by using <xref:System.Data.Linq.DataLoadOptions>.</span></span> <span data-ttu-id="deab9-109">Para obter mais informações, veja [carregamento deferido versus imediato](deferred-versus-immediate-loading.md).</span><span class="sxs-lookup"><span data-stu-id="deab9-109">For more information, see [Deferred versus Immediate Loading](deferred-versus-immediate-loading.md).</span></span>  
  
## <a name="partial-methods"></a><span data-ttu-id="deab9-110">Métodos parciais</span><span class="sxs-lookup"><span data-stu-id="deab9-110">Partial Methods</span></span>  
 <span data-ttu-id="deab9-111">No mapeamento padrão, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] fornece métodos parciais para ajudá-lo a implementar a lógica corporativa.</span><span class="sxs-lookup"><span data-stu-id="deab9-111">In its default mapping, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides partial methods to help you implement your business logic.</span></span> <span data-ttu-id="deab9-112">Para obter mais informações, consulte [adicionando lógica de negócios usando métodos parciais](adding-business-logic-by-using-partial-methods.md).</span><span class="sxs-lookup"><span data-stu-id="deab9-112">For more information, see [Adding Business Logic By Using Partial Methods](adding-business-logic-by-using-partial-methods.md).</span></span>  
  
## <a name="stored-procedures-and-user-defined-functions"></a><span data-ttu-id="deab9-113">Procedimentos e funções definidas pelo usuário armazenados</span><span class="sxs-lookup"><span data-stu-id="deab9-113">Stored Procedures and User-Defined Functions</span></span>  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="deab9-114">dá suporte ao uso de procedimentos armazenados e funções definidas pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="deab9-114">supports the use of stored procedures and user-defined functions.</span></span> <span data-ttu-id="deab9-115">Os procedimentos armazenados são usados para personalizar operações.</span><span class="sxs-lookup"><span data-stu-id="deab9-115">Stored procedures are frequently used to customize operations.</span></span> <span data-ttu-id="deab9-116">Para obter mais informações, consulte [Procedimentos armazenados](stored-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="deab9-116">For more information, see [Stored Procedures](stored-procedures.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="deab9-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="deab9-117">See also</span></span>

- [<span data-ttu-id="deab9-118">Personalizando as operações de inserção, atualização e exclusão</span><span class="sxs-lookup"><span data-stu-id="deab9-118">Customizing Insert, Update, and Delete Operations</span></span>](customizing-insert-update-and-delete-operations.md)
