---
title: <userDefinedType>
ms.date: 03/30/2017
ms.assetid: 0f70ec06-8249-4f0c-9f49-b4df59985fb8
ms.openlocfilehash: d1a48fa2ed90999a66f4c1f84b7cfaa9a0e79f6a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940577"
---
# <a name="userdefinedtype"></a><span data-ttu-id="0b03f-101">\<userDefinedType></span><span class="sxs-lookup"><span data-stu-id="0b03f-101">\<userDefinedType></span></span>
<span data-ttu-id="0b03f-102">Representa um tipo definido pelo usuário (UDT) que deve ser incluído no contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="0b03f-102">Represents a User Defined Type (UDT) that is to be included in the service contract.</span></span>  
  
 <span data-ttu-id="0b03f-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="0b03f-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="0b03f-104">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="0b03f-104">\<comContracts></span></span>  
<span data-ttu-id="0b03f-105">\<> de descontrato</span><span class="sxs-lookup"><span data-stu-id="0b03f-105">\<comContract></span></span>  
<span data-ttu-id="0b03f-106">\<userDefinedTypes></span><span class="sxs-lookup"><span data-stu-id="0b03f-106">\<userDefinedTypes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b03f-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0b03f-107">Syntax</span></span>  
  
```xml  
<comContracts>
  <comContract>
    <userDefinedTypes>
      <userDefinedType name="String"
                       typeLibID="String"
                       typeLibVersion="String"
                       typeDefID="String">
      </userDefinedType>
    </userDefinedTypes>
  </comContract>
</comContracts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0b03f-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="0b03f-108">Attributes and Elements</span></span>  
 <span data-ttu-id="0b03f-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="0b03f-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0b03f-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="0b03f-110">Attributes</span></span>  
  
|<span data-ttu-id="0b03f-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="0b03f-111">Attribute</span></span>|<span data-ttu-id="0b03f-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="0b03f-112">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="0b03f-113">Um atributo opcional que contém uma cadeia de caracteres que fornece o nome de tipo legível.</span><span class="sxs-lookup"><span data-stu-id="0b03f-113">An optional attribute that contains a string that provides the readable type name.</span></span> <span data-ttu-id="0b03f-114">Isso não é usado pelo tempo de execução, mas ajuda um leitor a distinguir os tipos.</span><span class="sxs-lookup"><span data-stu-id="0b03f-114">This is not used by the runtime but helps a reader to distinguish the types.</span></span>|  
|`TypeDefID`|<span data-ttu-id="0b03f-115">Uma cadeia de caracteres GUID que identifica o tipo UDT específico dentro da biblioteca de tipos registrada.</span><span class="sxs-lookup"><span data-stu-id="0b03f-115">A GUID string that identifies the specific UDT type within the registered type library.</span></span>|  
|`TypeLibID`|<span data-ttu-id="0b03f-116">Uma cadeia de caracteres GUID que identifica a biblioteca de tipos registrada que define o tipo.</span><span class="sxs-lookup"><span data-stu-id="0b03f-116">A GUID string that identifies the registered type library that defines the type.</span></span>|  
|`TypeLibVersion`|<span data-ttu-id="0b03f-117">Uma cadeia de caracteres que identifica a versão da biblioteca de tipos que define o tipo.</span><span class="sxs-lookup"><span data-stu-id="0b03f-117">A string that identifies the type library version that defines the type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0b03f-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="0b03f-118">Child Elements</span></span>  
 <span data-ttu-id="0b03f-119">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="0b03f-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0b03f-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="0b03f-120">Parent Elements</span></span>  
  
|<span data-ttu-id="0b03f-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="0b03f-121">Element</span></span>|<span data-ttu-id="0b03f-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="0b03f-122">Description</span></span>|  
|-------------|-----------------|  
|`userDefinedTypes`|<span data-ttu-id="0b03f-123">Uma coleção de elementos `userDefinedType`.</span><span class="sxs-lookup"><span data-stu-id="0b03f-123">A collection of `userDefinedType` elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0b03f-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="0b03f-124">Remarks</span></span>  
 <span data-ttu-id="0b03f-125">O Integration Runtime do COM+ cria serviços inspecionando a biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="0b03f-125">The COM+ integration runtime creates services by inspecting the type library.</span></span> <span data-ttu-id="0b03f-126">Quando um componente COM+ contém métodos que passam por uma variante, o sistema não pode determinar os tipos reais a serem passados antes do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="0b03f-126">When a COM+ component contains methods that pass a VARIANT, the system cannot determine the actual types to be passed prior to runtime.</span></span> <span data-ttu-id="0b03f-127">Portanto, quando você tenta passar um UDT (tipo definido pelo usuário) em uma variante, ele falha porque não é um tipo conhecido para serialização.</span><span class="sxs-lookup"><span data-stu-id="0b03f-127">Therefore, when you attempt to pass a User Defined Type (UDT) within a VARIANT, it fails because it is not a known type for serialization.</span></span>  
  
 <span data-ttu-id="0b03f-128">Para evitar esse problema, você pode adicionar os UDTs ao arquivo de configuração para que eles possam ser incluídos como tipos conhecidos no contrato de serviço apropriado.</span><span class="sxs-lookup"><span data-stu-id="0b03f-128">To circumvent this problem, you can add the UDTs to the configuration file so that they can be included as known types on the appropriate service contract.</span></span> <span data-ttu-id="0b03f-129">Para fazer isso, você precisa identificar exclusivamente o UDT e os contratos, ou seja, as interfaces COM originais que o usam....</span><span class="sxs-lookup"><span data-stu-id="0b03f-129">In order to do so, you have to uniquely identify the UDT and the contract(s), that is, the original COM interface(s) that uses it.</span></span>  
  
 <span data-ttu-id="0b03f-130">O exemplo a seguir demonstra como adicionar dois UDTs específicos à`userDefinedTypes`seção < > do arquivo de configuração para essa finalidade.</span><span class="sxs-lookup"><span data-stu-id="0b03f-130">The following example demonstrates adding two specific UDTs to the <`userDefinedTypes`> section of the configuration file for this purpose.</span></span>  
  
```xml  
<comContracts>
  <comContract contract="{5163B1E7-F0CF-4B6A-9A02-4AB654F34284}"
               namespace="http://tempuri.org/5163B1E7-F0CF-4B6A-9A02-4AB654F34284"
               name="_Broker"
               requireSession="true">
    <userDefinedTypes>
      <userDefinedType name="CustomerType"
                       typeLibID="{91DC728C-4F1A-45de-A9B6-B538E209CEA6}"
                       typeLibVersion="1.0"
                       typeDefID="{D129765C-F211-434e-825A-9A63198C41F2}">
      </userDefinedType>
      <userDefinedType name="AddressType"
                       typeLibID="{91DC728C-4F1A-45de-A9B6-B538E209CEA6}"
                       typeLibVersion="1.0"
                       typeDefID="{4616AE0D-687A-43B7-BC63-141AE3DFD099}">
      </userDefinedType>
    </userDefinedTypes>
    <exposedMethods>
      <exposedMethod name="BuyStock" />
      <exposedMethod name="SellStock" />
      <exposedMethod name="ExecuteTransaction" />
    </exposedMethods>
  </comContract>
</comContracts>
```  
  
 <span data-ttu-id="0b03f-131">Quando o serviço é inicializado, o Integration Runtime pesquisa os tipos especificados e os adiciona à coleção de tipos conhecidos para os contratos especificados.</span><span class="sxs-lookup"><span data-stu-id="0b03f-131">When the service is initialized, the integration runtime looks up the specified types and adds them to the known types collection for the specified contracts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b03f-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0b03f-132">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComContractElement.UserDefinedTypes%2A>
- <xref:System.ServiceModel.Configuration.ComUdtElementCollection>
- <xref:System.ServiceModel.Configuration.ComUdtElement>
- [<span data-ttu-id="0b03f-133">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="0b03f-133">\<comContracts></span></span>](comcontracts.md)
- [<span data-ttu-id="0b03f-134">Integração de aplicativos COM+</span><span class="sxs-lookup"><span data-stu-id="0b03f-134">Integrating with COM+ Applications</span></span>](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="0b03f-135">Como: Definir configurações de serviço COM+</span><span class="sxs-lookup"><span data-stu-id="0b03f-135">How to: Configure COM+ Service Settings</span></span>](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
