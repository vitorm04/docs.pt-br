---
title: < elemento de > Crst_DisableSpinWait
ms.date: 04/18/2019
f1_keywords:
- Crst_DisableSpinWait
helpviewer_keywords:
- Crst_DisableSpinWait element
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8a91e21120ecebbe7af2fb93798bc68d274fa92c
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252723"
---
# <a name="crst_disablespinwait-element"></a><span data-ttu-id="61435-102">\<Elemento de > Crst_DisableSpinWait</span><span class="sxs-lookup"><span data-stu-id="61435-102">\<Crst_DisableSpinWait> element</span></span>

<span data-ttu-id="61435-103">Especifica se é para desabilitar a espera de rotação para uma seção crítica quando contendeda.</span><span class="sxs-lookup"><span data-stu-id="61435-103">Specifies whether to disable spin-waiting for a critical section when contended.</span></span>  
  
<span data-ttu-id="61435-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="61435-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="61435-105">&nbsp;&nbsp;[ **\<> de tempo de execução**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="61435-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="61435-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<> Crst_DisableSpinWait**</span><span class="sxs-lookup"><span data-stu-id="61435-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<Crst_DisableSpinWait>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61435-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="61435-107">Syntax</span></span>  
  
```xml  
<Crst_DisableSpinWait enabled="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="61435-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="61435-108">Attributes and Elements</span></span>

<span data-ttu-id="61435-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="61435-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="61435-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="61435-110">Attributes</span></span>  
  
|<span data-ttu-id="61435-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="61435-111">Attribute</span></span>|<span data-ttu-id="61435-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="61435-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="61435-113">**habilitado**</span><span class="sxs-lookup"><span data-stu-id="61435-113">**enabled**</span></span>|<span data-ttu-id="61435-114">Especifica se a rotação-aguardando seções críticas quando elas são contendedas está desabilitada.</span><span class="sxs-lookup"><span data-stu-id="61435-114">Specifies whether spin-waiting for critical sections when they are contended is disabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="61435-115">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="61435-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="61435-116">Valor</span><span class="sxs-lookup"><span data-stu-id="61435-116">Value</span></span>|<span data-ttu-id="61435-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="61435-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="61435-118">1</span><span class="sxs-lookup"><span data-stu-id="61435-118">1</span></span>|<span data-ttu-id="61435-119">Desabilitar giro-aguardando quando uma seção crítica não puder ser adquirida.</span><span class="sxs-lookup"><span data-stu-id="61435-119">Disable spin-waiting when a critical section cannot be acquired.</span></span>|  
|<span data-ttu-id="61435-120">0</span><span class="sxs-lookup"><span data-stu-id="61435-120">0</span></span>|<span data-ttu-id="61435-121">Não desabilite o giro-aguardando quando uma seção crítica não puder ser adquirida.</span><span class="sxs-lookup"><span data-stu-id="61435-121">Do not disable spin-waiting when a critical section cannot be acquired.</span></span> <span data-ttu-id="61435-122">Este é o valor padrão.</span><span class="sxs-lookup"><span data-stu-id="61435-122">This is the default value.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="61435-123">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="61435-123">Child Elements</span></span>  
 <span data-ttu-id="61435-124">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="61435-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="61435-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="61435-125">Parent Elements</span></span>  
  
|<span data-ttu-id="61435-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="61435-126">Element</span></span>|<span data-ttu-id="61435-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="61435-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="61435-128">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="61435-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="61435-129">Contém informações sobre várias definições de configuração de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="61435-129">Contains information about various runtime configuration settings.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="61435-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="61435-130">Example</span></span>  

<span data-ttu-id="61435-131">O exemplo a seguir desabilita a espera de rotação em seções críticas quando contendeda.</span><span class="sxs-lookup"><span data-stu-id="61435-131">The following example disables spin-waiting in critical sections when contended.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <Crst_DisableSpinWait enabled="1"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="61435-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="61435-132">See also</span></span>

- [<span data-ttu-id="61435-133">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="61435-133">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="61435-134">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="61435-134">Configuration File Schema</span></span>](../index.md)
