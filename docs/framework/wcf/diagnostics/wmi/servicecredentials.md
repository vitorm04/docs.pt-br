---
title: ServiceCredentials
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9c780793-4785-46f7-add9-ac1ebeadb614
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 73fad36b5bf14745ca70d297fa988b90d46990df
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="servicecredentials"></a><span data-ttu-id="1679b-102">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="1679b-102">ServiceCredentials</span></span>
<span data-ttu-id="1679b-103">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="1679b-103">ServiceCredentials</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1679b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1679b-104">Syntax</span></span>  
  
```  
class ServiceCredentials : Behavior  
{  
  string ClientCertificate;  
  string IssuedTokenAuthentication;  
  string Peer;  
  string SecureConversationAuthentication;  
  string ServiceCertificate;  
  string UserNameAuthentication;  
  string WindowsAuthentication;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="1679b-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="1679b-105">Methods</span></span>  
 <span data-ttu-id="1679b-106">A classe ServiceCredentials não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="1679b-106">The ServiceCredentials class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="1679b-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="1679b-107">Properties</span></span>  
 <span data-ttu-id="1679b-108">A classe ServiceCredentials tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="1679b-108">The ServiceCredentials class has the following properties:</span></span>  
  
### <a name="clientcertificate"></a><span data-ttu-id="1679b-109">ClientCertificate</span><span class="sxs-lookup"><span data-stu-id="1679b-109">ClientCertificate</span></span>  
 <span data-ttu-id="1679b-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="1679b-110">Data type: string</span></span>  
  
 <span data-ttu-id="1679b-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="1679b-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1679b-112">Os certificado de provisionamento e autenticação de configurações do cliente para esse serviço.</span><span class="sxs-lookup"><span data-stu-id="1679b-112">The client certificate authentication and provisioning settings for this service.</span></span>  
  
### <a name="issuedtokenauthentication"></a><span data-ttu-id="1679b-113">IssuedTokenAuthentication</span><span class="sxs-lookup"><span data-stu-id="1679b-113">IssuedTokenAuthentication</span></span>  
 <span data-ttu-id="1679b-114">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="1679b-114">Data type: string</span></span>  
  
 <span data-ttu-id="1679b-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="1679b-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1679b-116">Atual emitido configurações de autenticação de token para este serviço.</span><span class="sxs-lookup"><span data-stu-id="1679b-116">The current issued token authentication settings for this service.</span></span>  
  
### <a name="peer"></a><span data-ttu-id="1679b-117">ponto a ponto</span><span class="sxs-lookup"><span data-stu-id="1679b-117">Peer</span></span>  
 <span data-ttu-id="1679b-118">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="1679b-118">Data type: string</span></span>  
  
 <span data-ttu-id="1679b-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="1679b-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1679b-120">Configurações a serem usadas pelos pontos de extremidade de transporte de par de provisionamento e autenticação de credencial atual.</span><span class="sxs-lookup"><span data-stu-id="1679b-120">The current credential authentication and provisioning settings to be used by peer transport endpoints.</span></span>  
  
### <a name="secureconversationauthentication"></a><span data-ttu-id="1679b-121">SecureConversationAuthentication</span><span class="sxs-lookup"><span data-stu-id="1679b-121">SecureConversationAuthentication</span></span>  
 <span data-ttu-id="1679b-122">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="1679b-122">Data type: string</span></span>  
  
 <span data-ttu-id="1679b-123">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="1679b-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1679b-124">Especifica as configurações atuais de conversa segura.</span><span class="sxs-lookup"><span data-stu-id="1679b-124">Specifies the current secure conversation settings.</span></span>  
  
### <a name="servicecertificate"></a><span data-ttu-id="1679b-125">ServiceCertificate</span><span class="sxs-lookup"><span data-stu-id="1679b-125">ServiceCertificate</span></span>  
 <span data-ttu-id="1679b-126">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="1679b-126">Data type: string</span></span>  
  
 <span data-ttu-id="1679b-127">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="1679b-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1679b-128">O certificado associado a esse serviço.</span><span class="sxs-lookup"><span data-stu-id="1679b-128">The certificate associated with this service.</span></span>  
  
### <a name="usernameauthentication"></a><span data-ttu-id="1679b-129">UserNameAuthentication</span><span class="sxs-lookup"><span data-stu-id="1679b-129">UserNameAuthentication</span></span>  
 <span data-ttu-id="1679b-130">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="1679b-130">Data type: string</span></span>  
  
 <span data-ttu-id="1679b-131">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="1679b-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1679b-132">As configurações de nome de usuário e senha para este serviço.</span><span class="sxs-lookup"><span data-stu-id="1679b-132">The username/password settings for this service.</span></span>  
  
### <a name="windowsauthentication"></a><span data-ttu-id="1679b-133">WindowsAuthentication</span><span class="sxs-lookup"><span data-stu-id="1679b-133">WindowsAuthentication</span></span>  
 <span data-ttu-id="1679b-134">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="1679b-134">Data type: string</span></span>  
  
 <span data-ttu-id="1679b-135">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="1679b-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1679b-136">As configurações de autenticação do Windows para este serviço.</span><span class="sxs-lookup"><span data-stu-id="1679b-136">The Windows authentication settings for this service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1679b-137">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1679b-137">Requirements</span></span>  
  
|<span data-ttu-id="1679b-138">MOF</span><span class="sxs-lookup"><span data-stu-id="1679b-138">MOF</span></span>|<span data-ttu-id="1679b-139">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="1679b-139">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="1679b-140">Namespace</span><span class="sxs-lookup"><span data-stu-id="1679b-140">Namespace</span></span>|<span data-ttu-id="1679b-141">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="1679b-141">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1679b-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1679b-142">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceCredentials>
