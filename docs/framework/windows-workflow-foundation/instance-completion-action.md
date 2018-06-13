---
title: Ação de conclusão da instância
ms.date: 03/30/2017
ms.assetid: 90cc99d2-9fef-42fd-bcbf-a56917993721
ms.openlocfilehash: 646015fbcdb7c734ae8584c7ca3979d64b81339f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33513195"
---
# <a name="instance-completion-action"></a><span data-ttu-id="bee5a-102">Ação de conclusão da instância</span><span class="sxs-lookup"><span data-stu-id="bee5a-102">Instance Completion Action</span></span>
<span data-ttu-id="bee5a-103">O **ação de conclusão de instância** propriedade do repositório de instância de fluxo de trabalho de SQL permite que você especifique se os dados e metadados de instâncias de fluxo de trabalho é excluído do banco de dados de persistência depois de concluir as instâncias.</span><span class="sxs-lookup"><span data-stu-id="bee5a-103">The **Instance Completion Action** property of the SQL Workflow Instance Store lets you specify whether the data and metadata of workflow instances is deleted from the persistence database after the instances are completed.</span></span> <span data-ttu-id="bee5a-104">Os valores permitidos para essa propriedade são **DeleteAll** e **DeleteNothing**.</span><span class="sxs-lookup"><span data-stu-id="bee5a-104">The allowed values for this property are **DeleteAll** and **DeleteNothing**.</span></span> <span data-ttu-id="bee5a-105">A lista a seguir descreve as opções:</span><span class="sxs-lookup"><span data-stu-id="bee5a-105">The following list describes these options:</span></span>  
  
-   <span data-ttu-id="bee5a-106">**DeleteAll (padrão).**</span><span class="sxs-lookup"><span data-stu-id="bee5a-106">**DeleteAll (default).**</span></span> <span data-ttu-id="bee5a-107">Se o valor da propriedade é definido como DeleteAll, os dados e os metadados de instâncias de fluxo de trabalho são excluídos de base de dados de persistência depois que as instâncias são concluídas.</span><span class="sxs-lookup"><span data-stu-id="bee5a-107">If the value of the property is set to DeleteAll, the data and metadata of workflow instances is deleted from the persistence database after the instances are completed.</span></span>  
  
-   <span data-ttu-id="bee5a-108">**DeleteNothing.**</span><span class="sxs-lookup"><span data-stu-id="bee5a-108">**DeleteNothing.**</span></span> <span data-ttu-id="bee5a-109">Se o valor da propriedade é definida como DeleteNothing, os dados e os metadados de instâncias de fluxo de trabalho são mantidos na base de dados de persistência mesmo após as instâncias são concluídas.</span><span class="sxs-lookup"><span data-stu-id="bee5a-109">If the value of the property is set to DeleteNothing, the data and metadata of workflow instances is kept in the persistence database even after the instances are completed.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="bee5a-110">Mantendo informações de estado da instância depois que as instâncias são causas concluídas o base de dados de persistência crescer em tamanho.</span><span class="sxs-lookup"><span data-stu-id="bee5a-110">Keeping instance state information after the instances are completed causes the persistence database to grow in size.</span></span> <span data-ttu-id="bee5a-111">Como o tamanho de base de dados cresce as operações de base de dados que o subsistema de persistência executa levam mais tempo, portanto você precisa limpar periodicamente informações de estado da instância de base de dados de persistência para que os serviços executar a nível que satisfazem às suas necessidades de desempenho.</span><span class="sxs-lookup"><span data-stu-id="bee5a-111">As the size of the database grows the database operations that the persistence subsystem performs take longer, so you need to purge the instance state information from the persistence database periodically to have services perform at the level that satisfy your performance needs.</span></span>
