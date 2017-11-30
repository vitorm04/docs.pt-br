---
title: TransactionFlowBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0a9656fe-2400-45ca-ad79-92715c8cf190
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4c65eb1689d1411cb9083967b9a29c946b7568b7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="transactionflowbindingelement"></a><span data-ttu-id="2b29a-102">TransactionFlowBindingElement</span><span class="sxs-lookup"><span data-stu-id="2b29a-102">TransactionFlowBindingElement</span></span>
<span data-ttu-id="2b29a-103">TransactionFlowBindingElement</span><span class="sxs-lookup"><span data-stu-id="2b29a-103">TransactionFlowBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b29a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2b29a-104">Syntax</span></span>  
  
```  
class TransactionFlowBindingElement : BindingElement  
{  
  string IssuedTokens;  
  string TransactionProtocol;  
  boolean Transactions;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="2b29a-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="2b29a-105">Methods</span></span>  
 <span data-ttu-id="2b29a-106">A classe TransactionFlowBindingElement não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="2b29a-106">The TransactionFlowBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="2b29a-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="2b29a-107">Properties</span></span>  
 <span data-ttu-id="2b29a-108">A classe TransactionFlowBindingElement tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="2b29a-108">The TransactionFlowBindingElement class has the following properties:</span></span>  
  
### <a name="issuedtokens"></a><span data-ttu-id="2b29a-109">IssuedTokens</span><span class="sxs-lookup"><span data-stu-id="2b29a-109">IssuedTokens</span></span>  
 <span data-ttu-id="2b29a-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="2b29a-110">Data type: string</span></span>  
  
 <span data-ttu-id="2b29a-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="2b29a-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2b29a-112">Especifica o requisito para um cabeçalho de tokens de segurança emitidos (IssuedTokens do WS-Trust).</span><span class="sxs-lookup"><span data-stu-id="2b29a-112">Specifies the requirement for an issued security tokens header (IssuedTokens from WS-Trust).</span></span>  
  
### <a name="transactionprotocol"></a><span data-ttu-id="2b29a-113">transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="2b29a-113">TransactionProtocol</span></span>  
 <span data-ttu-id="2b29a-114">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="2b29a-114">Data type: string</span></span>  
  
 <span data-ttu-id="2b29a-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="2b29a-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2b29a-116">O protocolo de transações usado pelo serviço para transações de fluxo.</span><span class="sxs-lookup"><span data-stu-id="2b29a-116">The transactions protocol used by the service to flow transactions.</span></span>  
  
### <a name="transactions"></a><span data-ttu-id="2b29a-117">Transações</span><span class="sxs-lookup"><span data-stu-id="2b29a-117">Transactions</span></span>  
 <span data-ttu-id="2b29a-118">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="2b29a-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="2b29a-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="2b29a-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2b29a-120">Indica se a transação de entrada tem suporte.</span><span class="sxs-lookup"><span data-stu-id="2b29a-120">Indicates whether the incoming transaction is supported.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b29a-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2b29a-121">Requirements</span></span>  
  
|<span data-ttu-id="2b29a-122">MOF</span><span class="sxs-lookup"><span data-stu-id="2b29a-122">MOF</span></span>|<span data-ttu-id="2b29a-123">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="2b29a-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="2b29a-124">Namespace</span><span class="sxs-lookup"><span data-stu-id="2b29a-124">Namespace</span></span>|<span data-ttu-id="2b29a-125">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="2b29a-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2b29a-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2b29a-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>
