---
title: Personalizando a inserção, atualiazação, e as operações de exclusão
ms.date: 03/30/2017
ms.assetid: 07eef055-8f6c-414d-850e-d323ff946cd0
ms.openlocfilehash: b4578a030300872bf4e0bab30b8daf12544be0cf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62032756"
---
# <a name="customizing-insert-update-and-delete-operations"></a><span data-ttu-id="3223e-102">Personalizando a inserção, atualiazação, e as operações de exclusão</span><span class="sxs-lookup"><span data-stu-id="3223e-102">Customizing Insert, Update, and Delete Operations</span></span>
<span data-ttu-id="3223e-103">Por padrão, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] gerencia dinâmico SQL para implementar à leitura, inserção, atualiazação, e as operações de exclusão.</span><span class="sxs-lookup"><span data-stu-id="3223e-103">By default, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generates dynamic SQL to implement insert, read, update, and delete operations.</span></span> <span data-ttu-id="3223e-104">Na prática, no entanto, você personaliza normalmente seu aplicativo atender às suas necessidades comerciais.</span><span class="sxs-lookup"><span data-stu-id="3223e-104">In practice, however, you typically customize your application to suit your business needs.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3223e-105">Se você estiver usando o Visual Studio, você pode usar o [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] para personalizar a inserir, atualizar e excluir ações.</span><span class="sxs-lookup"><span data-stu-id="3223e-105">If you are using Visual Studio, you can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to customize insert, update, and delete actions.</span></span>  
  
 <span data-ttu-id="3223e-106">Tópicos desta seção descreve as técnicas que [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] fornece personalizando à leitura, inserção, atualiazação, e as operações de exclusão em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3223e-106">This section of topics describes the techniques that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides for customizing insert, read, update, and delete operations in your application.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3223e-107">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="3223e-107">In This Section</span></span>  
 [<span data-ttu-id="3223e-108">Personalizando operações: visão geral</span><span class="sxs-lookup"><span data-stu-id="3223e-108">Customizing Operations: Overview</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-overview.md)  
 <span data-ttu-id="3223e-109">Descreve as diversas técnicas que [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] fornece personalizando à leitura, inserção, atualiazação, e as operações de exclusão.</span><span class="sxs-lookup"><span data-stu-id="3223e-109">Describes the various techniques [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides for customizing insert, read, update, and delete operations.</span></span>  
  
 [<span data-ttu-id="3223e-110">Operações de inserção, atualização e exclusão</span><span class="sxs-lookup"><span data-stu-id="3223e-110">Insert, Update, and Delete Operations</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/insert-update-and-delete-operations.md)  
 <span data-ttu-id="3223e-111">Descreve os processos de opção de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] para manipular dados de base de dados.</span><span class="sxs-lookup"><span data-stu-id="3223e-111">Describes the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default processes for manipulating database data.</span></span>  
  
 [<span data-ttu-id="3223e-112">Responsabilidades do desenvolvedor em substituir o comportamento padrão</span><span class="sxs-lookup"><span data-stu-id="3223e-112">Responsibilities of the Developer In Overriding Default Behavior</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md)  
 <span data-ttu-id="3223e-113">Descreve a função do desenvolvedor em implementar os requisitos não aplicadas por [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3223e-113">Describes the role of the developer in implementing requirements not enforced by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 [<span data-ttu-id="3223e-114">Adicionando a lógica de negócios usando métodos parciais</span><span class="sxs-lookup"><span data-stu-id="3223e-114">Adding Business Logic By Using Partial Methods</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md)  
 <span data-ttu-id="3223e-115">Descreve como usar os métodos parciais para substituir métodos gerado automaticamente.</span><span class="sxs-lookup"><span data-stu-id="3223e-115">Describes how to use partial methods to override autogenerated methods.</span></span>
