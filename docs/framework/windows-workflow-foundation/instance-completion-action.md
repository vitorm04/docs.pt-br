---
title: "Ação de conclusão da instância"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 90cc99d2-9fef-42fd-bcbf-a56917993721
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 83dec7ef4c911c0bca94caf7cc4c4bf832c8e1b6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="instance-completion-action"></a><span data-ttu-id="073d7-102">Ação de conclusão da instância</span><span class="sxs-lookup"><span data-stu-id="073d7-102">Instance Completion Action</span></span>
<span data-ttu-id="073d7-103">O **ação de conclusão de instância** propriedade do repositório de instância de fluxo de trabalho de SQL permite que você especifique se os dados e metadados de instâncias de fluxo de trabalho é excluído do banco de dados de persistência depois de concluir as instâncias.</span><span class="sxs-lookup"><span data-stu-id="073d7-103">The **Instance Completion Action** property of the SQL Workflow Instance Store lets you specify whether the data and metadata of workflow instances is deleted from the persistence database after the instances are completed.</span></span> <span data-ttu-id="073d7-104">Os valores permitidos para essa propriedade são **DeleteAll** e **DeleteNothing**.</span><span class="sxs-lookup"><span data-stu-id="073d7-104">The allowed values for this property are **DeleteAll** and **DeleteNothing**.</span></span> <span data-ttu-id="073d7-105">A lista a seguir descreve as opções:</span><span class="sxs-lookup"><span data-stu-id="073d7-105">The following list describes these options:</span></span>  
  
-   <span data-ttu-id="073d7-106">**DeleteAll (padrão).**</span><span class="sxs-lookup"><span data-stu-id="073d7-106">**DeleteAll (default).**</span></span> <span data-ttu-id="073d7-107">Se o valor da propriedade é definido como DeleteAll, os dados e os metadados de instâncias de fluxo de trabalho são excluídos de base de dados de persistência depois que as instâncias são concluídas.</span><span class="sxs-lookup"><span data-stu-id="073d7-107">If the value of the property is set to DeleteAll, the data and metadata of workflow instances is deleted from the persistence database after the instances are completed.</span></span>  
  
-   <span data-ttu-id="073d7-108">**DeleteNothing.**</span><span class="sxs-lookup"><span data-stu-id="073d7-108">**DeleteNothing.**</span></span> <span data-ttu-id="073d7-109">Se o valor da propriedade é definida como DeleteNothing, os dados e os metadados de instâncias de fluxo de trabalho são mantidos na base de dados de persistência mesmo após as instâncias são concluídas.</span><span class="sxs-lookup"><span data-stu-id="073d7-109">If the value of the property is set to DeleteNothing, the data and metadata of workflow instances is kept in the persistence database even after the instances are completed.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="073d7-110">Mantendo informações de estado da instância depois que as instâncias são causas concluídas o base de dados de persistência crescer em tamanho.</span><span class="sxs-lookup"><span data-stu-id="073d7-110">Keeping instance state information after the instances are completed causes the persistence database to grow in size.</span></span> <span data-ttu-id="073d7-111">Como o tamanho de base de dados cresce as operações de base de dados que o subsistema de persistência executa levam mais tempo, portanto você precisa limpar periodicamente informações de estado da instância de base de dados de persistência para que os serviços executar a nível que satisfazem às suas necessidades de desempenho.</span><span class="sxs-lookup"><span data-stu-id="073d7-111">As the size of the database grows the database operations that the persistence subsystem performs take longer, so you need to purge the instance state information from the persistence database periodically to have services perform at the level that satisfy your performance needs.</span></span>
