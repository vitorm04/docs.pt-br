---
title: elemento < Crst_DisableSpinWait >
ms.date: 04/18/2019
f1_keywords:
- Crst_DisableSpinWait
helpviewer_keywords:
- Crst_DisableSpinWait element
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6cde26250db0b3d11c51a18b7ebd378953ae0958
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704824"
---
# <a name="crstdisablespinwait-element"></a><span data-ttu-id="8cc54-102">\<Crst_DisableSpinWait > elemento</span><span class="sxs-lookup"><span data-stu-id="8cc54-102">\<Crst_DisableSpinWait> element</span></span>

<span data-ttu-id="8cc54-103">Especifica se é necessário desabilitar rotação-aguardando uma seção crítica quando sustentados.</span><span class="sxs-lookup"><span data-stu-id="8cc54-103">Specifies whether to disable spin-waiting for a critical section when contended.</span></span> \ 
  
 <span data-ttu-id="8cc54-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="8cc54-104">\<configuration></span></span>  
<span data-ttu-id="8cc54-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="8cc54-105">\<runtime></span></span>  
<span data-ttu-id="8cc54-106">\<Crst_DisableSpinWait></span><span class="sxs-lookup"><span data-stu-id="8cc54-106">\<Crst_DisableSpinWait></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8cc54-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8cc54-107">Syntax</span></span>  
  
```xml  
<Crst_DisableSpinWait enabled="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8cc54-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="8cc54-108">Attributes and Elements</span></span>

<span data-ttu-id="8cc54-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="8cc54-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8cc54-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="8cc54-110">Attributes</span></span>  
  
|<span data-ttu-id="8cc54-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="8cc54-111">Attribute</span></span>|<span data-ttu-id="8cc54-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="8cc54-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8cc54-113">**enabled**</span><span class="sxs-lookup"><span data-stu-id="8cc54-113">**enabled**</span></span>|<span data-ttu-id="8cc54-114">Especifica se a espera de rotação para seções críticas está habilitada quando eles são sustentados.</span><span class="sxs-lookup"><span data-stu-id="8cc54-114">Specifies whether spin-waiting for critical sections is enabled when they are contended.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="8cc54-115">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="8cc54-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="8cc54-116">Valor</span><span class="sxs-lookup"><span data-stu-id="8cc54-116">Value</span></span>|<span data-ttu-id="8cc54-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="8cc54-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8cc54-118">1</span><span class="sxs-lookup"><span data-stu-id="8cc54-118">1</span></span>|<span data-ttu-id="8cc54-119">Espera de rotação é habilitada.</span><span class="sxs-lookup"><span data-stu-id="8cc54-119">Spin-waiting is enabled.</span></span>|  
|<span data-ttu-id="8cc54-120">0</span><span class="sxs-lookup"><span data-stu-id="8cc54-120">0</span></span>|<span data-ttu-id="8cc54-121">Espera de rotação está desabilitada.</span><span class="sxs-lookup"><span data-stu-id="8cc54-121">Spin-waiting is disabled.</span></span> <span data-ttu-id="8cc54-122">Esse é o padrão</span><span class="sxs-lookup"><span data-stu-id="8cc54-122">This is the default</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8cc54-123">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="8cc54-123">Child Elements</span></span>  
 <span data-ttu-id="8cc54-124">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="8cc54-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8cc54-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="8cc54-125">Parent Elements</span></span>  
  
|<span data-ttu-id="8cc54-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="8cc54-126">Element</span></span>|<span data-ttu-id="8cc54-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="8cc54-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="8cc54-128">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8cc54-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="8cc54-129">Contém informações sobre várias definições de configuração de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="8cc54-129">Contains information about various runtime configuration settings.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="8cc54-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8cc54-130">Example</span></span>  

<span data-ttu-id="8cc54-131">A exemplo a seguir desabilita espera de rotação em seções críticas quando sustentados.</span><span class="sxs-lookup"><span data-stu-id="8cc54-131">The following example disables spin-waiting in critical sections when contended.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <Crst_DisableSpinWait enabled="1"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8cc54-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8cc54-132">See also</span></span>

- [<span data-ttu-id="8cc54-133">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="8cc54-133">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="8cc54-134">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="8cc54-134">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
