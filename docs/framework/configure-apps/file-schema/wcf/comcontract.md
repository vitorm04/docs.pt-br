---
title: <comContract>
ms.date: 03/30/2017
ms.assetid: 3f8e1c0c-cfdf-4c79-ac65-c64e9323a51c
ms.openlocfilehash: ef980c86efad4fda86cf62148e50688fd22afe49
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926098"
---
# <a name="comcontract"></a><span data-ttu-id="a2ad9-101">\<> de descontrato</span><span class="sxs-lookup"><span data-stu-id="a2ad9-101">\<comContract></span></span>
<span data-ttu-id="a2ad9-102">Especifica um contrato de serviço de integração COM+.</span><span class="sxs-lookup"><span data-stu-id="a2ad9-102">Specifies a COM+ integration service contract.</span></span>  
  
 <span data-ttu-id="a2ad9-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a2ad9-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="a2ad9-104">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="a2ad9-104">\<comContracts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2ad9-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a2ad9-105">Syntax</span></span>  
  
```xml  
<comContracts>
  <comContract contract="String"
               namespace="String"
               name="String"
               requireSession="Boolean">
    <exposedMethods>
      <exposedMethod name="String" />
    </exposedMethods>
    <userDefinedTypes>
      <userDefinedType name="String"
                       typeLibID="String"
                       typeLibVersion="String"
                       typeDefID="String">
      </userDefinedType>
    </userDefinedTypes>
    <persistableTypes>
      <persistableType id="String"
                       name="String">
      </persistableType>
    </persistableTypes>
  </comContract>
</comContracts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a2ad9-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a2ad9-106">Attributes and Elements</span></span>  
 <span data-ttu-id="a2ad9-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="a2ad9-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a2ad9-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="a2ad9-108">Attributes</span></span>  
  
|<span data-ttu-id="a2ad9-109">Atributo</span><span class="sxs-lookup"><span data-stu-id="a2ad9-109">Attribute</span></span>|<span data-ttu-id="a2ad9-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="a2ad9-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a2ad9-111">contrato</span><span class="sxs-lookup"><span data-stu-id="a2ad9-111">contract</span></span>|<span data-ttu-id="a2ad9-112">Uma cadeia de caracteres que contém o tipo de contrato.</span><span class="sxs-lookup"><span data-stu-id="a2ad9-112">A string that contains the contract type.</span></span>|  
|<span data-ttu-id="a2ad9-113">name</span><span class="sxs-lookup"><span data-stu-id="a2ad9-113">name</span></span>|<span data-ttu-id="a2ad9-114">Uma cadeia de caracteres que contém o nome do contrato.</span><span class="sxs-lookup"><span data-stu-id="a2ad9-114">A string that contains the contract name.</span></span>|  
|<span data-ttu-id="a2ad9-115">namespace</span><span class="sxs-lookup"><span data-stu-id="a2ad9-115">namespace</span></span>|<span data-ttu-id="a2ad9-116">Uma cadeia de caracteres que contém o namespace do contrato.</span><span class="sxs-lookup"><span data-stu-id="a2ad9-116">A string that contains the contract namespace.</span></span>|  
|<span data-ttu-id="a2ad9-117">requiresSession</span><span class="sxs-lookup"><span data-stu-id="a2ad9-117">requiresSession</span></span>|<span data-ttu-id="a2ad9-118">Um valor booliano que especifica se o contrato só pode ser usado em associações de sessão.</span><span class="sxs-lookup"><span data-stu-id="a2ad9-118">A Boolean value that specifies whether the contract can only be used on sessionful bindings.</span></span> <span data-ttu-id="a2ad9-119">Quando o serviço é inicializado, o Integration Runtime garante que essa configuração seja consistente com o tipo de associação a ser usada.</span><span class="sxs-lookup"><span data-stu-id="a2ad9-119">When the service is initialized, the integration runtime ensures that this setting is consistent with the type of binding to be used.</span></span> <span data-ttu-id="a2ad9-120">Uma exceção será gerada se uma ou mais das associações para o contrato estiverem em conflito.</span><span class="sxs-lookup"><span data-stu-id="a2ad9-120">An exception is generated if one or more of the bindings for the contract are in conflict.</span></span> <span data-ttu-id="a2ad9-121">Se essa propriedade for `false`, e um canal unidirecional estiver em uso e houver quaisquer parâmetros [out], uma exceção também será gerada.</span><span class="sxs-lookup"><span data-stu-id="a2ad9-121">If this property is `false`, and a one-way channel is in use and there are any [out] parameters, an exception is also generated.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a2ad9-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a2ad9-122">Child Elements</span></span>  
  
|<span data-ttu-id="a2ad9-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="a2ad9-123">Element</span></span>|<span data-ttu-id="a2ad9-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="a2ad9-124">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a2ad9-125">persistableTypes</span><span class="sxs-lookup"><span data-stu-id="a2ad9-125">persistableTypes</span></span>|<span data-ttu-id="a2ad9-126">Todos os tipos persistentes.</span><span class="sxs-lookup"><span data-stu-id="a2ad9-126">All the persistable types.</span></span>|  
|<span data-ttu-id="a2ad9-127">userDefinedTypes</span><span class="sxs-lookup"><span data-stu-id="a2ad9-127">userDefinedTypes</span></span>|<span data-ttu-id="a2ad9-128">Uma coleção de tipos definidos pelo usuário (UDT) que deve ser incluída no contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="a2ad9-128">A collection of User Defined Types (UDT) that is to be included in the service contract.</span></span>|  
|<span data-ttu-id="a2ad9-129">exposedMethods</span><span class="sxs-lookup"><span data-stu-id="a2ad9-129">exposedMethods</span></span>|<span data-ttu-id="a2ad9-130">Uma coleção de métodos COM+ que são expostos quando a interface em um componente COM+ é exposta como um serviço Web.</span><span class="sxs-lookup"><span data-stu-id="a2ad9-130">A collection of COM+ methods that are exposed when the interface on a COM+ component is exposed as a Web service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a2ad9-131">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a2ad9-131">Parent Elements</span></span>  
  
|<span data-ttu-id="a2ad9-132">Elemento</span><span class="sxs-lookup"><span data-stu-id="a2ad9-132">Element</span></span>|<span data-ttu-id="a2ad9-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="a2ad9-133">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a2ad9-134">comContracts</span><span class="sxs-lookup"><span data-stu-id="a2ad9-134">comContracts</span></span>|<span data-ttu-id="a2ad9-135">Contém uma coleção de `comContract` elementos.</span><span class="sxs-lookup"><span data-stu-id="a2ad9-135">Contains a collection of `comContract` elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a2ad9-136">Comentários</span><span class="sxs-lookup"><span data-stu-id="a2ad9-136">Remarks</span></span>  
 <span data-ttu-id="a2ad9-137">Os contratos do serviço de `http://tempuri.org` integração com+ estão atualmente restritos ao namespace e o nome do contrato é derivado da interface com de suporte.</span><span class="sxs-lookup"><span data-stu-id="a2ad9-137">COM+ integration service contracts are currently restricted to the `http://tempuri.org` namespace, and contract name is derived from the supporting COM interface.</span></span> <span data-ttu-id="a2ad9-138">No entanto, você pode especificar alternativas usando a `comContracts` seção, bem como o `comContract` elemento no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="a2ad9-138">You can, however, specify alternatives by using the `comContracts` section, as well as the `comContract` element in the configuration file.</span></span> <span data-ttu-id="a2ad9-139">Por exemplo, você pode usar a configuração a seguir para especificar o namespace, o nome do contrato e os tipos definidos pelo usuário a serem incluídos, bem como outras configurações para um contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="a2ad9-139">For example, you can use the following configuration to specify the namespace, contract name, and user defined types to be included, as well as other settings for a service contract.</span></span>  
  
```xml  
<comContracts>
  <comContract contract="{5163B1E7-F0CF-4B6A-9A02-4AB654F34284}"
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
  
 <span data-ttu-id="a2ad9-140">Quando o serviço é inicializado, os namespaces e os nomes de contrato especificados são aplicados às descrições de serviço geradas.</span><span class="sxs-lookup"><span data-stu-id="a2ad9-140">When the service is initialized, the specified namespaces and contract names are applied to the generated service descriptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2ad9-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a2ad9-141">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComContractElementCollection>
- <xref:System.ServiceModel.Configuration.ComContractElement>
- [<span data-ttu-id="a2ad9-142">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="a2ad9-142">\<comContracts></span></span>](comcontracts.md)
- [<span data-ttu-id="a2ad9-143">Integração de aplicativos COM+</span><span class="sxs-lookup"><span data-stu-id="a2ad9-143">Integrating with COM+ Applications</span></span>](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="a2ad9-144">Como: Definir configurações de serviço COM+</span><span class="sxs-lookup"><span data-stu-id="a2ad9-144">How to: Configure COM+ Service Settings</span></span>](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
