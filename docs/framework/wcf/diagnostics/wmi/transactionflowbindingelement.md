---
title: TransactionFlowBindingElement
ms.date: 03/30/2017
ms.assetid: 0a9656fe-2400-45ca-ad79-92715c8cf190
ms.openlocfilehash: d0311837ebb8112d9492fb548492bcd3e10230e7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54514563"
---
# <a name="transactionflowbindingelement"></a><span data-ttu-id="77c72-102">TransactionFlowBindingElement</span><span class="sxs-lookup"><span data-stu-id="77c72-102">TransactionFlowBindingElement</span></span>
<span data-ttu-id="77c72-103">TransactionFlowBindingElement</span><span class="sxs-lookup"><span data-stu-id="77c72-103">TransactionFlowBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77c72-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="77c72-104">Syntax</span></span>  
  
```csharp
class TransactionFlowBindingElement : BindingElement  
{  
  string IssuedTokens;  
  string TransactionProtocol;  
  boolean Transactions;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="77c72-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="77c72-105">Methods</span></span>  
 <span data-ttu-id="77c72-106">A classe TransactionFlowBindingElement não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="77c72-106">The TransactionFlowBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="77c72-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="77c72-107">Properties</span></span>  
 <span data-ttu-id="77c72-108">A classe TransactionFlowBindingElement tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="77c72-108">The TransactionFlowBindingElement class has the following properties:</span></span>  
  
### <a name="issuedtokens"></a><span data-ttu-id="77c72-109">IssuedTokens</span><span class="sxs-lookup"><span data-stu-id="77c72-109">IssuedTokens</span></span>  
 <span data-ttu-id="77c72-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="77c72-110">Data type: string</span></span>  
  
 <span data-ttu-id="77c72-111">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="77c72-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="77c72-112">Especifica o requisito para um cabeçalho de tokens de segurança emitido (IssuedTokens do WS-Trust).</span><span class="sxs-lookup"><span data-stu-id="77c72-112">Specifies the requirement for an issued security tokens header (IssuedTokens from WS-Trust).</span></span>  
  
### <a name="transactionprotocol"></a><span data-ttu-id="77c72-113">TransactionProtocol</span><span class="sxs-lookup"><span data-stu-id="77c72-113">TransactionProtocol</span></span>  
 <span data-ttu-id="77c72-114">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="77c72-114">Data type: string</span></span>  
  
 <span data-ttu-id="77c72-115">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="77c72-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="77c72-116">O protocolo de transações usado pelo serviço para transações de fluxo.</span><span class="sxs-lookup"><span data-stu-id="77c72-116">The transactions protocol used by the service to flow transactions.</span></span>  
  
### <a name="transactions"></a><span data-ttu-id="77c72-117">Transações</span><span class="sxs-lookup"><span data-stu-id="77c72-117">Transactions</span></span>  
 <span data-ttu-id="77c72-118">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="77c72-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="77c72-119">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="77c72-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="77c72-120">Indica se a transação de entrada tem suporte.</span><span class="sxs-lookup"><span data-stu-id="77c72-120">Indicates whether the incoming transaction is supported.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77c72-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="77c72-121">Requirements</span></span>  
  
|<span data-ttu-id="77c72-122">MOF</span><span class="sxs-lookup"><span data-stu-id="77c72-122">MOF</span></span>|<span data-ttu-id="77c72-123">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="77c72-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="77c72-124">Namespace</span><span class="sxs-lookup"><span data-stu-id="77c72-124">Namespace</span></span>|<span data-ttu-id="77c72-125">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="77c72-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="77c72-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="77c72-126">See also</span></span>
- <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>
