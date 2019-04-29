---
title: TransactionFlowBindingElement
ms.date: 03/30/2017
ms.assetid: 0a9656fe-2400-45ca-ad79-92715c8cf190
ms.openlocfilehash: a58d5620abbb636480ceea3020552246ae284842
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61641678"
---
# <a name="transactionflowbindingelement"></a><span data-ttu-id="ad0f8-102">TransactionFlowBindingElement</span><span class="sxs-lookup"><span data-stu-id="ad0f8-102">TransactionFlowBindingElement</span></span>
<span data-ttu-id="ad0f8-103">TransactionFlowBindingElement</span><span class="sxs-lookup"><span data-stu-id="ad0f8-103">TransactionFlowBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad0f8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ad0f8-104">Syntax</span></span>  
  
```csharp
class TransactionFlowBindingElement : BindingElement  
{  
  string IssuedTokens;  
  string TransactionProtocol;  
  boolean Transactions;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="ad0f8-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="ad0f8-105">Methods</span></span>  
 <span data-ttu-id="ad0f8-106">A classe TransactionFlowBindingElement não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="ad0f8-106">The TransactionFlowBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="ad0f8-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="ad0f8-107">Properties</span></span>  
 <span data-ttu-id="ad0f8-108">A classe TransactionFlowBindingElement tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="ad0f8-108">The TransactionFlowBindingElement class has the following properties:</span></span>  
  
### <a name="issuedtokens"></a><span data-ttu-id="ad0f8-109">IssuedTokens</span><span class="sxs-lookup"><span data-stu-id="ad0f8-109">IssuedTokens</span></span>  
 <span data-ttu-id="ad0f8-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="ad0f8-110">Data type: string</span></span>  
  
 <span data-ttu-id="ad0f8-111">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="ad0f8-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ad0f8-112">Especifica o requisito para um cabeçalho de tokens de segurança emitido (IssuedTokens do WS-Trust).</span><span class="sxs-lookup"><span data-stu-id="ad0f8-112">Specifies the requirement for an issued security tokens header (IssuedTokens from WS-Trust).</span></span>  
  
### <a name="transactionprotocol"></a><span data-ttu-id="ad0f8-113">TransactionProtocol</span><span class="sxs-lookup"><span data-stu-id="ad0f8-113">TransactionProtocol</span></span>  
 <span data-ttu-id="ad0f8-114">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="ad0f8-114">Data type: string</span></span>  
  
 <span data-ttu-id="ad0f8-115">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="ad0f8-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ad0f8-116">O protocolo de transações usado pelo serviço para transações de fluxo.</span><span class="sxs-lookup"><span data-stu-id="ad0f8-116">The transactions protocol used by the service to flow transactions.</span></span>  
  
### <a name="transactions"></a><span data-ttu-id="ad0f8-117">Transações</span><span class="sxs-lookup"><span data-stu-id="ad0f8-117">Transactions</span></span>  
 <span data-ttu-id="ad0f8-118">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="ad0f8-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="ad0f8-119">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="ad0f8-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ad0f8-120">Indica se a transação de entrada tem suporte.</span><span class="sxs-lookup"><span data-stu-id="ad0f8-120">Indicates whether the incoming transaction is supported.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad0f8-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ad0f8-121">Requirements</span></span>  
  
|<span data-ttu-id="ad0f8-122">MOF</span><span class="sxs-lookup"><span data-stu-id="ad0f8-122">MOF</span></span>|<span data-ttu-id="ad0f8-123">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="ad0f8-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="ad0f8-124">Namespace</span><span class="sxs-lookup"><span data-stu-id="ad0f8-124">Namespace</span></span>|<span data-ttu-id="ad0f8-125">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="ad0f8-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ad0f8-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ad0f8-126">See also</span></span>

- <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>
