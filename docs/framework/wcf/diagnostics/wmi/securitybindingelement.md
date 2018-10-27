---
title: SecurityBindingElement
ms.date: 03/30/2017
ms.assetid: ef93b6e6-3524-48a8-94d3-c8837f1872f9
ms.openlocfilehash: 601e3fafd9aa876186b7f78dfdcb87a2336ddfcd
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50185765"
---
# <a name="securitybindingelement"></a><span data-ttu-id="051c6-102">SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="051c6-102">SecurityBindingElement</span></span>
<span data-ttu-id="051c6-103">SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="051c6-103">SecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="051c6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="051c6-104">Syntax</span></span>  
  
```csharp
class SecurityBindingElement : BindingElement  
{  
  string DefaultAlgorithmSuite;  
  boolean IncludeTimestamp;  
  string KeyEntropyMode;  
  LocalServiceSecuritySettings LocalServiceSecuritySettings;  
  string MessageSecurityVersion;  
  string SecurityHeaderLayout;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="051c6-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="051c6-105">Methods</span></span>  
 <span data-ttu-id="051c6-106">A classe SecurityBindingElement não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="051c6-106">The SecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="051c6-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="051c6-107">Properties</span></span>  
 <span data-ttu-id="051c6-108">A classe SecurityBindingElement tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="051c6-108">The SecurityBindingElement class has the following properties:</span></span>  
  
### <a name="defaultalgorithmsuite"></a><span data-ttu-id="051c6-109">defaultAlgorithmSuite</span><span class="sxs-lookup"><span data-stu-id="051c6-109">DefaultAlgorithmSuite</span></span>  
 <span data-ttu-id="051c6-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="051c6-110">Data type: string</span></span>  
  
 <span data-ttu-id="051c6-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="051c6-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="051c6-112">Especifica os algoritmos para usar com a associação.</span><span class="sxs-lookup"><span data-stu-id="051c6-112">Specifies the algorithms to use with the binding.</span></span>  
  
### <a name="includetimestamp"></a><span data-ttu-id="051c6-113">includeTimestamp</span><span class="sxs-lookup"><span data-stu-id="051c6-113">IncludeTimestamp</span></span>  
 <span data-ttu-id="051c6-114">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="051c6-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="051c6-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="051c6-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="051c6-116">Um valor booliano que especifica se cada mensagem contém um carimbo de hora.</span><span class="sxs-lookup"><span data-stu-id="051c6-116">A Boolean value that specifies whether each message contains a timestamp.</span></span>  
  
### <a name="keyentropymode"></a><span data-ttu-id="051c6-117">keyEntropyMode</span><span class="sxs-lookup"><span data-stu-id="051c6-117">KeyEntropyMode</span></span>  
 <span data-ttu-id="051c6-118">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="051c6-118">Data type: string</span></span>  
  
 <span data-ttu-id="051c6-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="051c6-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="051c6-120">A origem da entropia usada para criar chaves.</span><span class="sxs-lookup"><span data-stu-id="051c6-120">The source of entropy used to create keys.</span></span>  
  
### <a name="localservicesecuritysettings"></a><span data-ttu-id="051c6-121">LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="051c6-121">LocalServiceSecuritySettings</span></span>  
 <span data-ttu-id="051c6-122">Tipo de dados: LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="051c6-122">Data type: LocalServiceSecuritySettings</span></span>  
  
 <span data-ttu-id="051c6-123">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="051c6-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="051c6-124">As propriedades específicas de segurança de associação para o serviço local.</span><span class="sxs-lookup"><span data-stu-id="051c6-124">The binding specific security properties for the local service.</span></span>  
  
### <a name="messagesecurityversion"></a><span data-ttu-id="051c6-125">messageSecurityVersion</span><span class="sxs-lookup"><span data-stu-id="051c6-125">MessageSecurityVersion</span></span>  
 <span data-ttu-id="051c6-126">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="051c6-126">Data type: string</span></span>  
  
 <span data-ttu-id="051c6-127">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="051c6-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="051c6-128">A versão usada para segurança de mensagem.</span><span class="sxs-lookup"><span data-stu-id="051c6-128">The version used for message security.</span></span>  
  
### <a name="securityheaderlayout"></a><span data-ttu-id="051c6-129">securityHeaderLayout</span><span class="sxs-lookup"><span data-stu-id="051c6-129">SecurityHeaderLayout</span></span>  
 <span data-ttu-id="051c6-130">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="051c6-130">Data type: string</span></span>  
  
 <span data-ttu-id="051c6-131">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="051c6-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="051c6-132">A ordem dos elementos no cabeçalho de segurança para essa associação.</span><span class="sxs-lookup"><span data-stu-id="051c6-132">The order of elements in the security header for this binding.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="051c6-133">Requisitos</span><span class="sxs-lookup"><span data-stu-id="051c6-133">Requirements</span></span>  
  
|<span data-ttu-id="051c6-134">MOF</span><span class="sxs-lookup"><span data-stu-id="051c6-134">MOF</span></span>|<span data-ttu-id="051c6-135">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="051c6-135">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="051c6-136">Namespace</span><span class="sxs-lookup"><span data-stu-id="051c6-136">Namespace</span></span>|<span data-ttu-id="051c6-137">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="051c6-137">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="051c6-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="051c6-138">See Also</span></span>  
 <xref:System.ServiceModel.Channels.SecurityBindingElement>
