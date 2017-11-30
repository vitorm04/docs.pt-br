---
title: "Segurança"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 737ec121-bfc5-4b75-a504-2d53c2c8af39
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a17b77293d9a12fd3720fc54cb6c17a28a8c6ed0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="security"></a><span data-ttu-id="73713-102">Segurança</span><span class="sxs-lookup"><span data-stu-id="73713-102">Security</span></span>
<span data-ttu-id="73713-103">A instância Store de fluxo de trabalho do SQL usa as seguintes funções de segurança de base de dados para proteger o acesso a informações do estado da instância na base de dados de persistência.</span><span class="sxs-lookup"><span data-stu-id="73713-103">The SQL Workflow Instance Store uses the following database security roles to secure access to instance state information in the persistence database.</span></span>  
  
-   <span data-ttu-id="73713-104">**System.Activities.DurableInstancing.InstanceStoreUsers**.</span><span class="sxs-lookup"><span data-stu-id="73713-104">**System.Activities.DurableInstancing.InstanceStoreUsers**.</span></span> <span data-ttu-id="73713-105">Essa função tem acesso de leitura e gravação para a exibição e a direita públicas de execução procedimentos armazenados que estão envolvidos na criação, em carregar e salvar em instâncias.</span><span class="sxs-lookup"><span data-stu-id="73713-105">This role has read and write access to public views and execution rights to stored procedures that are involved in creating, loading and saving instances.</span></span>  
  
-   <span data-ttu-id="73713-106">**System.Activities.DurableInstancing.InstanceStoreObservers**.</span><span class="sxs-lookup"><span data-stu-id="73713-106">**System.Activities.DurableInstancing.InstanceStoreObservers**.</span></span> <span data-ttu-id="73713-107">Essa função tem acesso somente leitura modos de exibição públicas.</span><span class="sxs-lookup"><span data-stu-id="73713-107">This role has read-only access to public views.</span></span>  
  
-   <span data-ttu-id="73713-108">**System.Activities.DurableInstancing.WorkflowActivationUsers**.</span><span class="sxs-lookup"><span data-stu-id="73713-108">**System.Activities.DurableInstancing.WorkflowActivationUsers**.</span></span> <span data-ttu-id="73713-109">Essa função tem direitos de execução procedimentos armazenados que estão envolvidos no processo de ativação da instância.</span><span class="sxs-lookup"><span data-stu-id="73713-109">This role has execution rights to stored procedures that are involved in the instance activation process.</span></span> <span data-ttu-id="73713-110">Para obter mais informações sobre a ativação de instância, consulte [ativação de instância](../../../docs/framework/windows-workflow-foundation/instance-activation.md).</span><span class="sxs-lookup"><span data-stu-id="73713-110">For more information about instance activation, see [Instance Activation](../../../docs/framework/windows-workflow-foundation/instance-activation.md).</span></span> <span data-ttu-id="73713-111">A conta de usuário em que um host genérico (como o serviço de gerenciamento de fluxo de trabalho [!INCLUDE[dublin](../../../includes/dublin-md.md)]) executa deve ser adicionada à essa função de base de dados.</span><span class="sxs-lookup"><span data-stu-id="73713-111">The user account under which a generic host (such as the Workflow Management Service of [!INCLUDE[dublin](../../../includes/dublin-md.md)]) runs should be added to this database role.</span></span>  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="73713-112">segurança de persistência lojas com a malha de aplicativos do Windows Server, consulte [configuração de segurança para os armazenamentos de persistência na malha de aplicativos](http://go.microsoft.com/fwlink/?LinkId=201208)</span><span class="sxs-lookup"><span data-stu-id="73713-112"> security for persistence stores with Windows Server App Fabric, see [Security Configuration for Persistence Stores in App Fabric](http://go.microsoft.com/fwlink/?LinkId=201208)</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="73713-113">Um cliente que tenha acesso a seus próprios dados de instância no armazenamento de instância tem acesso a todas as outras instâncias no mesmo armazenamento de instância.</span><span class="sxs-lookup"><span data-stu-id="73713-113">A client that has access to its own instance data in the instance store has access to all other instances in the same instance store.</span></span> <span data-ttu-id="73713-114">O armazenamento de instância não suporta especificar permissões de segurança no nível da instância.</span><span class="sxs-lookup"><span data-stu-id="73713-114">The instance store does not support specifying security permissions at the instance level.</span></span> <span data-ttu-id="73713-115">Você deve criar armazenamentos separados de instância e mapear grupos/usuários diferentes para ter acesso aos armazenamentos diferentes.</span><span class="sxs-lookup"><span data-stu-id="73713-115">You should create separate instance stores and map different groups/users to have access to different stores.</span></span>
