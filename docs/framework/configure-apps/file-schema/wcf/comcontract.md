---
title: <comContract>
ms.date: 03/30/2017
ms.assetid: 3f8e1c0c-cfdf-4c79-ac65-c64e9323a51c
ms.openlocfilehash: b499294af71ba230dcf985d4af1d013b1ca260cf
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850033"
---
# \<comContract>
<span data-ttu-id="5f431-101">Especifica um contrato de serviço de integração COM+.</span><span class="sxs-lookup"><span data-stu-id="5f431-101">Specifies a COM+ integration service contract.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContracts>**](comcontracts.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<comContract>**  
  
## <a name="syntax"></a><span data-ttu-id="5f431-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5f431-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5f431-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="5f431-103">Attributes and Elements</span></span>  
 <span data-ttu-id="5f431-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="5f431-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5f431-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="5f431-105">Attributes</span></span>  
  
|<span data-ttu-id="5f431-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="5f431-106">Attribute</span></span>|<span data-ttu-id="5f431-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="5f431-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5f431-108">contrato</span><span class="sxs-lookup"><span data-stu-id="5f431-108">contract</span></span>|<span data-ttu-id="5f431-109">Uma cadeia de caracteres que contém o tipo de contrato.</span><span class="sxs-lookup"><span data-stu-id="5f431-109">A string that contains the contract type.</span></span>|  
|<span data-ttu-id="5f431-110">name</span><span class="sxs-lookup"><span data-stu-id="5f431-110">name</span></span>|<span data-ttu-id="5f431-111">Uma cadeia de caracteres que contém o nome do contrato.</span><span class="sxs-lookup"><span data-stu-id="5f431-111">A string that contains the contract name.</span></span>|  
|<span data-ttu-id="5f431-112">namespace</span><span class="sxs-lookup"><span data-stu-id="5f431-112">namespace</span></span>|<span data-ttu-id="5f431-113">Uma cadeia de caracteres que contém o namespace do contrato.</span><span class="sxs-lookup"><span data-stu-id="5f431-113">A string that contains the contract namespace.</span></span>|  
|<span data-ttu-id="5f431-114">requiresSession</span><span class="sxs-lookup"><span data-stu-id="5f431-114">requiresSession</span></span>|<span data-ttu-id="5f431-115">Um valor booliano que especifica se o contrato só pode ser usado em associações de sessão.</span><span class="sxs-lookup"><span data-stu-id="5f431-115">A Boolean value that specifies whether the contract can only be used on sessionful bindings.</span></span> <span data-ttu-id="5f431-116">Quando o serviço é inicializado, o Integration Runtime garante que essa configuração seja consistente com o tipo de associação a ser usada.</span><span class="sxs-lookup"><span data-stu-id="5f431-116">When the service is initialized, the integration runtime ensures that this setting is consistent with the type of binding to be used.</span></span> <span data-ttu-id="5f431-117">Uma exceção será gerada se uma ou mais das associações para o contrato estiverem em conflito.</span><span class="sxs-lookup"><span data-stu-id="5f431-117">An exception is generated if one or more of the bindings for the contract are in conflict.</span></span> <span data-ttu-id="5f431-118">Se essa propriedade for `false` , e um canal unidirecional estiver em uso e houver quaisquer parâmetros [out], uma exceção também será gerada.</span><span class="sxs-lookup"><span data-stu-id="5f431-118">If this property is `false`, and a one-way channel is in use and there are any [out] parameters, an exception is also generated.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5f431-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="5f431-119">Child Elements</span></span>  
  
|<span data-ttu-id="5f431-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="5f431-120">Element</span></span>|<span data-ttu-id="5f431-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="5f431-121">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5f431-122">persistableTypes</span><span class="sxs-lookup"><span data-stu-id="5f431-122">persistableTypes</span></span>|<span data-ttu-id="5f431-123">Todos os tipos persistentes.</span><span class="sxs-lookup"><span data-stu-id="5f431-123">All the persistable types.</span></span>|  
|<span data-ttu-id="5f431-124">userDefinedTypes</span><span class="sxs-lookup"><span data-stu-id="5f431-124">userDefinedTypes</span></span>|<span data-ttu-id="5f431-125">Uma coleção de tipos definidos pelo usuário (UDT) que deve ser incluída no contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="5f431-125">A collection of User Defined Types (UDT) that is to be included in the service contract.</span></span>|  
|<span data-ttu-id="5f431-126">exposedMethods</span><span class="sxs-lookup"><span data-stu-id="5f431-126">exposedMethods</span></span>|<span data-ttu-id="5f431-127">Uma coleção de métodos COM+ que são expostos quando a interface em um componente COM+ é exposta como um serviço Web.</span><span class="sxs-lookup"><span data-stu-id="5f431-127">A collection of COM+ methods that are exposed when the interface on a COM+ component is exposed as a Web service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5f431-128">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="5f431-128">Parent Elements</span></span>  
  
|<span data-ttu-id="5f431-129">Elemento</span><span class="sxs-lookup"><span data-stu-id="5f431-129">Element</span></span>|<span data-ttu-id="5f431-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="5f431-130">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5f431-131">comContracts</span><span class="sxs-lookup"><span data-stu-id="5f431-131">comContracts</span></span>|<span data-ttu-id="5f431-132">Contém uma coleção de `comContract` elementos.</span><span class="sxs-lookup"><span data-stu-id="5f431-132">Contains a collection of `comContract` elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5f431-133">Comentários</span><span class="sxs-lookup"><span data-stu-id="5f431-133">Remarks</span></span>  
 <span data-ttu-id="5f431-134">Os contratos do serviço de integração COM+ estão atualmente restritos ao `http://tempuri.org` namespace e o nome do contrato é derivado da interface com de suporte.</span><span class="sxs-lookup"><span data-stu-id="5f431-134">COM+ integration service contracts are currently restricted to the `http://tempuri.org` namespace, and contract name is derived from the supporting COM interface.</span></span> <span data-ttu-id="5f431-135">No entanto, você pode especificar alternativas usando a `comContracts` seção, bem como o `comContract` elemento no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="5f431-135">You can, however, specify alternatives by using the `comContracts` section, as well as the `comContract` element in the configuration file.</span></span> <span data-ttu-id="5f431-136">Por exemplo, você pode usar a configuração a seguir para especificar o namespace, o nome do contrato e os tipos definidos pelo usuário a serem incluídos, bem como outras configurações para um contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="5f431-136">For example, you can use the following configuration to specify the namespace, contract name, and user defined types to be included, as well as other settings for a service contract.</span></span>  
  
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
  
 <span data-ttu-id="5f431-137">Quando o serviço é inicializado, os namespaces e os nomes de contrato especificados são aplicados às descrições de serviço geradas.</span><span class="sxs-lookup"><span data-stu-id="5f431-137">When the service is initialized, the specified namespaces and contract names are applied to the generated service descriptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f431-138">Confira também</span><span class="sxs-lookup"><span data-stu-id="5f431-138">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComContractElementCollection>
- <xref:System.ServiceModel.Configuration.ComContractElement>
- [\<comContracts>](comcontracts.md)
- [<span data-ttu-id="5f431-139">Integração com aplicativos COM+</span><span class="sxs-lookup"><span data-stu-id="5f431-139">Integrating with COM+ Applications</span></span>](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="5f431-140">Como configurar configurações de serviço de COM+</span><span class="sxs-lookup"><span data-stu-id="5f431-140">How to: Configure COM+ Service Settings</span></span>](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
