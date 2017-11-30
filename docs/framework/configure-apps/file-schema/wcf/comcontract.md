---
title: '&lt;comContract&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3f8e1c0c-cfdf-4c79-ac65-c64e9323a51c
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b22c8d0b72d4dfc63eb5fa9afa073f993f75418e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltcomcontractgt"></a><span data-ttu-id="5c962-102">&lt;comContract&gt;</span><span class="sxs-lookup"><span data-stu-id="5c962-102">&lt;comContract&gt;</span></span>
<span data-ttu-id="5c962-103">Especifica um contrato de serviço de integração COM+.</span><span class="sxs-lookup"><span data-stu-id="5c962-103">Specifies a COM+ integration service contract.</span></span>  
  
 <span data-ttu-id="5c962-104">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="5c962-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="5c962-105">\<comContracts ></span><span class="sxs-lookup"><span data-stu-id="5c962-105">\<comContracts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c962-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5c962-106">Syntax</span></span>  
  
```xml  
<comContracts>  
  <comContract  
      contract="string"  
      namespace="string"  
      name="string"  
      requireSession="Boolean">  
      <exposedMethods>  
         <exposedMethod name="string" />  
      </exposedMethods>  
      <userDefinedTypes>  
         <userDefinedType name="string"  
            typeLibID="string"  
            typeLibVersion="string"  
            typeDefID="string">  
         </userDefinedType>  
      </userDefinedTypes>  
      <persistableTypes>  
         <persistableType id="string"  
            name="string">  
         </persistableType>  
      </persistableTypes>  
  </comContract>  
</comContracts>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5c962-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="5c962-107">Attributes and Elements</span></span>  
 <span data-ttu-id="5c962-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="5c962-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5c962-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="5c962-109">Attributes</span></span>  
  
|<span data-ttu-id="5c962-110">Atributo</span><span class="sxs-lookup"><span data-stu-id="5c962-110">Attribute</span></span>|<span data-ttu-id="5c962-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="5c962-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5c962-112">contrato</span><span class="sxs-lookup"><span data-stu-id="5c962-112">contract</span></span>|<span data-ttu-id="5c962-113">Uma cadeia de caracteres que contém o tipo de contrato.</span><span class="sxs-lookup"><span data-stu-id="5c962-113">A string that contains the contract type.</span></span>|  
|<span data-ttu-id="5c962-114">name</span><span class="sxs-lookup"><span data-stu-id="5c962-114">name</span></span>|<span data-ttu-id="5c962-115">Uma cadeia de caracteres que contém o nome do contrato.</span><span class="sxs-lookup"><span data-stu-id="5c962-115">A string that contains the contract name.</span></span>|  
|<span data-ttu-id="5c962-116">namespace</span><span class="sxs-lookup"><span data-stu-id="5c962-116">namespace</span></span>|<span data-ttu-id="5c962-117">Uma cadeia de caracteres que contém o namespace de contrato.</span><span class="sxs-lookup"><span data-stu-id="5c962-117">A string that contains the contract namespace.</span></span>|  
|<span data-ttu-id="5c962-118">requiresSession</span><span class="sxs-lookup"><span data-stu-id="5c962-118">requiresSession</span></span>|<span data-ttu-id="5c962-119">Um valor booleano que especifica se o contrato só pode ser usado em associações de sessão.</span><span class="sxs-lookup"><span data-stu-id="5c962-119">A Boolean value that specifies whether the contract can only be used on sessionful bindings.</span></span> <span data-ttu-id="5c962-120">Quando o serviço é inicializado, o tempo de execução de integração garante que essa configuração é consistente com o tipo de associação a ser usada.</span><span class="sxs-lookup"><span data-stu-id="5c962-120">When the service is initialized, the integration runtime ensures that this setting is consistent with the type of binding to be used.</span></span> <span data-ttu-id="5c962-121">Uma exceção será gerada se um ou mais associações para o contrato estão em conflito.</span><span class="sxs-lookup"><span data-stu-id="5c962-121">An exception is generated if one or more of the bindings for the contract are in conflict.</span></span> <span data-ttu-id="5c962-122">Se essa propriedade for `false`e um canal unidirecional está em uso e houver [parâmetros out], também será gerada uma exceção.</span><span class="sxs-lookup"><span data-stu-id="5c962-122">If this property is `false`, and a one-way channel is in use and there are any [out] parameters, an exception is also generated.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5c962-123">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="5c962-123">Child Elements</span></span>  
  
|<span data-ttu-id="5c962-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="5c962-124">Element</span></span>|<span data-ttu-id="5c962-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="5c962-125">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5c962-126">persistableTypes</span><span class="sxs-lookup"><span data-stu-id="5c962-126">persistableTypes</span></span>|<span data-ttu-id="5c962-127">Todos os tipos persistentes.</span><span class="sxs-lookup"><span data-stu-id="5c962-127">All the persistable types.</span></span>|  
|<span data-ttu-id="5c962-128">userDefinedTypes</span><span class="sxs-lookup"><span data-stu-id="5c962-128">userDefinedTypes</span></span>|<span data-ttu-id="5c962-129">Uma coleção de usuário definidos UDTS (tipos) que deve ser incluído no contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="5c962-129">A collection of User Defined Types (UDT) that is to be included in the service contract.</span></span>|  
|<span data-ttu-id="5c962-130">exposedMethods</span><span class="sxs-lookup"><span data-stu-id="5c962-130">exposedMethods</span></span>|<span data-ttu-id="5c962-131">Uma coleção de métodos COM+ expostos quando a interface em um componente COM+ é exposta como um serviço Web.</span><span class="sxs-lookup"><span data-stu-id="5c962-131">A collection of COM+ methods that are exposed when the interface on a COM+ component is exposed as a Web service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5c962-132">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="5c962-132">Parent Elements</span></span>  
  
|<span data-ttu-id="5c962-133">Elemento</span><span class="sxs-lookup"><span data-stu-id="5c962-133">Element</span></span>|<span data-ttu-id="5c962-134">Descrição</span><span class="sxs-lookup"><span data-stu-id="5c962-134">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5c962-135">comContracts</span><span class="sxs-lookup"><span data-stu-id="5c962-135">comContracts</span></span>|<span data-ttu-id="5c962-136">Contém uma coleção de `comContract` elementos.</span><span class="sxs-lookup"><span data-stu-id="5c962-136">Contains a collection of `comContract` elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5c962-137">Comentários</span><span class="sxs-lookup"><span data-stu-id="5c962-137">Remarks</span></span>  
 <span data-ttu-id="5c962-138">Contratos de serviço COM+ integration estão restritos atualmente para o namespace "http://tempuri.org" e nome de contrato é derivado da interface COM suporte.</span><span class="sxs-lookup"><span data-stu-id="5c962-138">COM+ integration service contracts are currently restricted to the "http://tempuri.org" namespace, and contract name is derived from the supporting COM interface.</span></span> <span data-ttu-id="5c962-139">No entanto, você pode especificar alternativas usando o `comContracts` seção, bem como a `comContract` elemento no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="5c962-139">You can, however, specify alternatives by using the `comContracts` section, as well as the `comContract` element in the configuration file.</span></span> <span data-ttu-id="5c962-140">Por exemplo, você pode usar a configuração a seguir para especificar o namespace, nome do contrato e tipos definidos pelo usuário a ser incluído, bem como outras configurações para um contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="5c962-140">For example, you can use the following configuration to specify the namespace, contract name, and user defined types to be included, as well as other settings for a service contract.</span></span>  
  
```xml  
<comContracts>  
  <comContract  
      contract="{5163B1E7-F0CF-4B6A-9A02-4AB654F34284}"  
      namespace="http://tempuri.org/5163B1E7-F0CF-4B6A-9A02-4AB654F34284"  
      name="_Broker"  
      requireSession="true">  
      <exposedMethods>  
         <exposedMethod name="BuyStock" />  
         <exposedMethod name="SellStock" />  
         <exposedMethod name="ExecuteTransaction" />  
      </exposedMethods>  
  </comContract>  
</comContracts>  
```  
  
 <span data-ttu-id="5c962-141">Quando o serviço é inicializado, os namespaces especificados e os nomes de contrato são aplicados as descrições de serviço gerado.</span><span class="sxs-lookup"><span data-stu-id="5c962-141">When the service is initialized, the specified namespaces and contract names are applied to the generated service descriptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c962-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5c962-142">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ComContractElementCollection>  
 <xref:System.ServiceModel.Configuration.ComContractElementCollection>  
 <xref:System.ServiceModel.Configuration.ComContractElement>  
 [<span data-ttu-id="5c962-143">\<comContracts ></span><span class="sxs-lookup"><span data-stu-id="5c962-143">\<comContracts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)  
 [<span data-ttu-id="5c962-144">Integrando aplicativos COM+</span><span class="sxs-lookup"><span data-stu-id="5c962-144">Integrating with COM+ Applications</span></span>](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [<span data-ttu-id="5c962-145">Como: definir configurações de serviço COM+</span><span class="sxs-lookup"><span data-stu-id="5c962-145">How to: Configure COM+ Service Settings</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
