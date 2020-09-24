---
title: <callbackDebug>
ms.date: 03/30/2017
ms.assetid: 4073feda-1857-4be4-9947-227afb847ced
ms.openlocfilehash: 02632cc3f668bb9e4cc6f8c9726d7bcb3cab2c5d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183813"
---
# \<callbackDebug>

<span data-ttu-id="0c3c2-101">Especifica a depuração de serviço para um objeto de retorno de chamada Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="0c3c2-101">Specifies service debugging for a Windows Communication Foundation (WCF) callback object.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<callbackDebug>**  
  
## <a name="syntax"></a><span data-ttu-id="0c3c2-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0c3c2-102">Syntax</span></span>  
  
```xml  
<callbackDebug includeExceptionDetailInFaults="Boolean" />
```  
  
## <a name="type"></a><span data-ttu-id="0c3c2-103">Tipo</span><span class="sxs-lookup"><span data-stu-id="0c3c2-103">Type</span></span>  

 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0c3c2-104">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="0c3c2-104">Attributes and Elements</span></span>  

 <span data-ttu-id="0c3c2-105">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="0c3c2-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0c3c2-106">Atributos</span><span class="sxs-lookup"><span data-stu-id="0c3c2-106">Attributes</span></span>  
  
|<span data-ttu-id="0c3c2-107">Atributo</span><span class="sxs-lookup"><span data-stu-id="0c3c2-107">Attribute</span></span>|<span data-ttu-id="0c3c2-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="0c3c2-108">Description</span></span>|  
|---------------|-----------------|  
|`includeExceptionDetailInFaults`|<span data-ttu-id="0c3c2-109">Um valor que especifica se os objetos de retorno de chamada do cliente retornam informações de exceção gerenciada em falhas de SOAP de volta ao serviço.</span><span class="sxs-lookup"><span data-stu-id="0c3c2-109">A value that specifies whether client callback objects return managed exception information in SOAP faults back to the service.</span></span><br /><br /> <span data-ttu-id="0c3c2-110">Se você definir esse atributo como `true` programaticamente, poderá habilitar o fluxo de informações de exceção gerenciada em um objeto de retorno de chamada do cliente de volta para o serviço para fins de depuração.</span><span class="sxs-lookup"><span data-stu-id="0c3c2-110">If you set this attribute to `true` programmatically, you can enable the flow of managed exception information in a client callback object back to the service for debugging purposes.</span></span> <span data-ttu-id="0c3c2-111">**Cuidado:**  Retornar informações de exceção gerenciada aos clientes pode ser um risco de segurança.</span><span class="sxs-lookup"><span data-stu-id="0c3c2-111">**Caution:**  Returning managed exception information to clients can be a security risk.</span></span> <span data-ttu-id="0c3c2-112">Isso ocorre porque os detalhes da exceção expõem informações sobre a implementação do serviço interno que pode ser usada por clientes não autorizados.</span><span class="sxs-lookup"><span data-stu-id="0c3c2-112">This is because exception details expose information about the internal service implementation that could be used by unauthorized clients.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0c3c2-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="0c3c2-113">Child Elements</span></span>  

 <span data-ttu-id="0c3c2-114">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="0c3c2-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0c3c2-115">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="0c3c2-115">Parent Elements</span></span>  
  
|<span data-ttu-id="0c3c2-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="0c3c2-116">Element</span></span>|<span data-ttu-id="0c3c2-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="0c3c2-117">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="0c3c2-118">Especifica um comportamento de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="0c3c2-118">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0c3c2-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="0c3c2-119">See also</span></span>

- <xref:System.ServiceModel.Configuration.CallbackDebugElement>
- <xref:System.ServiceModel.Description.CallbackDebugBehavior>
