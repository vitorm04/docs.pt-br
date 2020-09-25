---
title: Personalizando a inserção, atualiazação, e as operações de exclusão
ms.date: 03/30/2017
ms.assetid: 07eef055-8f6c-414d-850e-d323ff946cd0
ms.openlocfilehash: 4b846d1e1f737cec85ecda75df5e3f66982def62
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177339"
---
# <a name="customizing-insert-update-and-delete-operations"></a><span data-ttu-id="dc3f6-102">Personalizando a inserção, atualiazação, e as operações de exclusão</span><span class="sxs-lookup"><span data-stu-id="dc3f6-102">Customizing Insert, Update, and Delete Operations</span></span>

<span data-ttu-id="dc3f6-103">Por padrão, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] gerencia dinâmico SQL para implementar à leitura, inserção, atualiazação, e as operações de exclusão.</span><span class="sxs-lookup"><span data-stu-id="dc3f6-103">By default, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generates dynamic SQL to implement insert, read, update, and delete operations.</span></span> <span data-ttu-id="dc3f6-104">Na prática, no entanto, você personaliza normalmente seu aplicativo atender às suas necessidades comerciais.</span><span class="sxs-lookup"><span data-stu-id="dc3f6-104">In practice, however, you typically customize your application to suit your business needs.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dc3f6-105">Se você estiver usando o Visual Studio, poderá usar o Object Relational Designer para personalizar as ações de inserção, atualização e exclusão.</span><span class="sxs-lookup"><span data-stu-id="dc3f6-105">If you are using Visual Studio, you can use the Object Relational Designer to customize insert, update, and delete actions.</span></span>  
  
 <span data-ttu-id="dc3f6-106">Tópicos desta seção descreve as técnicas que [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] fornece personalizando à leitura, inserção, atualiazação, e as operações de exclusão em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="dc3f6-106">This section of topics describes the techniques that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides for customizing insert, read, update, and delete operations in your application.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="dc3f6-107">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="dc3f6-107">In This Section</span></span>  

 [<span data-ttu-id="dc3f6-108">Personalizar operações: Visão geral</span><span class="sxs-lookup"><span data-stu-id="dc3f6-108">Customizing Operations: Overview</span></span>](customizing-operations-overview.md)  
 <span data-ttu-id="dc3f6-109">Descreve as diversas técnicas que [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] fornece personalizando à leitura, inserção, atualiazação, e as operações de exclusão.</span><span class="sxs-lookup"><span data-stu-id="dc3f6-109">Describes the various techniques [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides for customizing insert, read, update, and delete operations.</span></span>  
  
 [<span data-ttu-id="dc3f6-110">Operações de inserção, atualização e exclusão</span><span class="sxs-lookup"><span data-stu-id="dc3f6-110">Insert, Update, and Delete Operations</span></span>](insert-update-and-delete-operations.md)  
 <span data-ttu-id="dc3f6-111">Descreve os processos de opção de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] para manipular dados de base de dados.</span><span class="sxs-lookup"><span data-stu-id="dc3f6-111">Describes the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default processes for manipulating database data.</span></span>  
  
 [<span data-ttu-id="dc3f6-112">Responsabilidades do desenvolvedor em substituir o comportamento padrão</span><span class="sxs-lookup"><span data-stu-id="dc3f6-112">Responsibilities of the Developer In Overriding Default Behavior</span></span>](responsibilities-of-the-developer-in-overriding-default-behavior.md)  
 <span data-ttu-id="dc3f6-113">Descreve a função do desenvolvedor em implementar os requisitos não aplicadas por [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="dc3f6-113">Describes the role of the developer in implementing requirements not enforced by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 [<span data-ttu-id="dc3f6-114">Adicionando a lógica comercial usando métodos parciais</span><span class="sxs-lookup"><span data-stu-id="dc3f6-114">Adding Business Logic By Using Partial Methods</span></span>](adding-business-logic-by-using-partial-methods.md)  
 <span data-ttu-id="dc3f6-115">Descreve como usar os métodos parciais para substituir métodos gerado automaticamente.</span><span class="sxs-lookup"><span data-stu-id="dc3f6-115">Describes how to use partial methods to override autogenerated methods.</span></span>
