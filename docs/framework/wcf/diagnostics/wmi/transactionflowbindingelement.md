---
title: TransactionFlowBindingElement
ms.date: 03/30/2017
ms.assetid: 0a9656fe-2400-45ca-ad79-92715c8cf190
ms.openlocfilehash: c2fb32c4c693cbfc487ce89b36f013398cbdb703
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33485613"
---
# <a name="transactionflowbindingelement"></a><span data-ttu-id="b78a0-102">TransactionFlowBindingElement</span><span class="sxs-lookup"><span data-stu-id="b78a0-102">TransactionFlowBindingElement</span></span>
<span data-ttu-id="b78a0-103">TransactionFlowBindingElement</span><span class="sxs-lookup"><span data-stu-id="b78a0-103">TransactionFlowBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b78a0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b78a0-104">Syntax</span></span>  
  
```  
class TransactionFlowBindingElement : BindingElement  
{  
  string IssuedTokens;  
  string TransactionProtocol;  
  boolean Transactions;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="b78a0-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="b78a0-105">Methods</span></span>  
 <span data-ttu-id="b78a0-106">A classe TransactionFlowBindingElement não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="b78a0-106">The TransactionFlowBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="b78a0-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="b78a0-107">Properties</span></span>  
 <span data-ttu-id="b78a0-108">A classe TransactionFlowBindingElement tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="b78a0-108">The TransactionFlowBindingElement class has the following properties:</span></span>  
  
### <a name="issuedtokens"></a><span data-ttu-id="b78a0-109">IssuedTokens</span><span class="sxs-lookup"><span data-stu-id="b78a0-109">IssuedTokens</span></span>  
 <span data-ttu-id="b78a0-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="b78a0-110">Data type: string</span></span>  
  
 <span data-ttu-id="b78a0-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="b78a0-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b78a0-112">Especifica o requisito para um cabeçalho de tokens de segurança emitidos (IssuedTokens do WS-Trust).</span><span class="sxs-lookup"><span data-stu-id="b78a0-112">Specifies the requirement for an issued security tokens header (IssuedTokens from WS-Trust).</span></span>  
  
### <a name="transactionprotocol"></a><span data-ttu-id="b78a0-113">transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="b78a0-113">TransactionProtocol</span></span>  
 <span data-ttu-id="b78a0-114">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="b78a0-114">Data type: string</span></span>  
  
 <span data-ttu-id="b78a0-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="b78a0-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b78a0-116">O protocolo de transações usado pelo serviço para transações de fluxo.</span><span class="sxs-lookup"><span data-stu-id="b78a0-116">The transactions protocol used by the service to flow transactions.</span></span>  
  
### <a name="transactions"></a><span data-ttu-id="b78a0-117">Transações</span><span class="sxs-lookup"><span data-stu-id="b78a0-117">Transactions</span></span>  
 <span data-ttu-id="b78a0-118">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="b78a0-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="b78a0-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="b78a0-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b78a0-120">Indica se a transação de entrada tem suporte.</span><span class="sxs-lookup"><span data-stu-id="b78a0-120">Indicates whether the incoming transaction is supported.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b78a0-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b78a0-121">Requirements</span></span>  
  
|<span data-ttu-id="b78a0-122">MOF</span><span class="sxs-lookup"><span data-stu-id="b78a0-122">MOF</span></span>|<span data-ttu-id="b78a0-123">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="b78a0-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="b78a0-124">Namespace</span><span class="sxs-lookup"><span data-stu-id="b78a0-124">Namespace</span></span>|<span data-ttu-id="b78a0-125">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="b78a0-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b78a0-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b78a0-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>
