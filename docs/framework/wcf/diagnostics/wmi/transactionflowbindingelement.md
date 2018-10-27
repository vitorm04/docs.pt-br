---
title: TransactionFlowBindingElement
ms.date: 03/30/2017
ms.assetid: 0a9656fe-2400-45ca-ad79-92715c8cf190
ms.openlocfilehash: 027ace6ea9fc2a0e5ce63efa84e1a49c0ed2cd0a
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50188021"
---
# <a name="transactionflowbindingelement"></a><span data-ttu-id="cec35-102">TransactionFlowBindingElement</span><span class="sxs-lookup"><span data-stu-id="cec35-102">TransactionFlowBindingElement</span></span>
<span data-ttu-id="cec35-103">TransactionFlowBindingElement</span><span class="sxs-lookup"><span data-stu-id="cec35-103">TransactionFlowBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cec35-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cec35-104">Syntax</span></span>  
  
```csharp
class TransactionFlowBindingElement : BindingElement  
{  
  string IssuedTokens;  
  string TransactionProtocol;  
  boolean Transactions;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="cec35-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="cec35-105">Methods</span></span>  
 <span data-ttu-id="cec35-106">A classe TransactionFlowBindingElement não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="cec35-106">The TransactionFlowBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="cec35-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="cec35-107">Properties</span></span>  
 <span data-ttu-id="cec35-108">A classe TransactionFlowBindingElement tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="cec35-108">The TransactionFlowBindingElement class has the following properties:</span></span>  
  
### <a name="issuedtokens"></a><span data-ttu-id="cec35-109">IssuedTokens</span><span class="sxs-lookup"><span data-stu-id="cec35-109">IssuedTokens</span></span>  
 <span data-ttu-id="cec35-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="cec35-110">Data type: string</span></span>  
  
 <span data-ttu-id="cec35-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="cec35-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cec35-112">Especifica o requisito para um cabeçalho de tokens de segurança emitido (IssuedTokens do WS-Trust).</span><span class="sxs-lookup"><span data-stu-id="cec35-112">Specifies the requirement for an issued security tokens header (IssuedTokens from WS-Trust).</span></span>  
  
### <a name="transactionprotocol"></a><span data-ttu-id="cec35-113">transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="cec35-113">TransactionProtocol</span></span>  
 <span data-ttu-id="cec35-114">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="cec35-114">Data type: string</span></span>  
  
 <span data-ttu-id="cec35-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="cec35-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cec35-116">O protocolo de transações usado pelo serviço para transações de fluxo.</span><span class="sxs-lookup"><span data-stu-id="cec35-116">The transactions protocol used by the service to flow transactions.</span></span>  
  
### <a name="transactions"></a><span data-ttu-id="cec35-117">Transações</span><span class="sxs-lookup"><span data-stu-id="cec35-117">Transactions</span></span>  
 <span data-ttu-id="cec35-118">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="cec35-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="cec35-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="cec35-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cec35-120">Indica se a transação de entrada tem suporte.</span><span class="sxs-lookup"><span data-stu-id="cec35-120">Indicates whether the incoming transaction is supported.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cec35-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cec35-121">Requirements</span></span>  
  
|<span data-ttu-id="cec35-122">MOF</span><span class="sxs-lookup"><span data-stu-id="cec35-122">MOF</span></span>|<span data-ttu-id="cec35-123">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="cec35-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="cec35-124">Namespace</span><span class="sxs-lookup"><span data-stu-id="cec35-124">Namespace</span></span>|<span data-ttu-id="cec35-125">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="cec35-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cec35-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cec35-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>
