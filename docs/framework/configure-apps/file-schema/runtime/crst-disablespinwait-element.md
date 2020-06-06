---
title: Elemento <Crst_DisableSpinWait>
ms.date: 04/18/2019
f1_keywords:
- Crst_DisableSpinWait
helpviewer_keywords:
- Crst_DisableSpinWait element
ms.openlocfilehash: 0683081183081e249b2a9c89e1a6a15f638fb339
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73117644"
---
# <a name="crst_disablespinwait-element"></a><span data-ttu-id="9849c-102">Elemento \<Crst_DisableSpinWait></span><span class="sxs-lookup"><span data-stu-id="9849c-102">\<Crst_DisableSpinWait> element</span></span>

<span data-ttu-id="9849c-103">Especifica se é para desabilitar a espera de rotação para uma seção crítica quando contendeda.</span><span class="sxs-lookup"><span data-stu-id="9849c-103">Specifies whether to disable spin-waiting for a critical section when contended.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<Crst_DisableSpinWait>**  
  
## <a name="syntax"></a><span data-ttu-id="9849c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9849c-104">Syntax</span></span>  
  
```xml  
<Crst_DisableSpinWait enabled="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9849c-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="9849c-105">Attributes and Elements</span></span>

<span data-ttu-id="9849c-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="9849c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9849c-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="9849c-107">Attributes</span></span>  
  
|<span data-ttu-id="9849c-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="9849c-108">Attribute</span></span>|<span data-ttu-id="9849c-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="9849c-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9849c-110">**habilitado**</span><span class="sxs-lookup"><span data-stu-id="9849c-110">**enabled**</span></span>|<span data-ttu-id="9849c-111">Especifica se a rotação-aguardando seções críticas quando elas são contendedas está desabilitada.</span><span class="sxs-lookup"><span data-stu-id="9849c-111">Specifies whether spin-waiting for critical sections when they are contended is disabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="9849c-112">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="9849c-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="9849c-113">Valor</span><span class="sxs-lookup"><span data-stu-id="9849c-113">Value</span></span>|<span data-ttu-id="9849c-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="9849c-114">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9849c-115">1</span><span class="sxs-lookup"><span data-stu-id="9849c-115">1</span></span>|<span data-ttu-id="9849c-116">Desabilitar giro-aguardando quando uma seção crítica não puder ser adquirida.</span><span class="sxs-lookup"><span data-stu-id="9849c-116">Disable spin-waiting when a critical section cannot be acquired.</span></span>|  
|<span data-ttu-id="9849c-117">0</span><span class="sxs-lookup"><span data-stu-id="9849c-117">0</span></span>|<span data-ttu-id="9849c-118">Não desabilite o giro-aguardando quando uma seção crítica não puder ser adquirida.</span><span class="sxs-lookup"><span data-stu-id="9849c-118">Do not disable spin-waiting when a critical section cannot be acquired.</span></span> <span data-ttu-id="9849c-119">Esse é o valor padrão.</span><span class="sxs-lookup"><span data-stu-id="9849c-119">This is the default value.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9849c-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="9849c-120">Child Elements</span></span>  
 <span data-ttu-id="9849c-121">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="9849c-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9849c-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="9849c-122">Parent Elements</span></span>  
  
|<span data-ttu-id="9849c-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="9849c-123">Element</span></span>|<span data-ttu-id="9849c-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="9849c-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="9849c-125">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9849c-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="9849c-126">Contém informações sobre várias definições de configuração de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="9849c-126">Contains information about various runtime configuration settings.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="9849c-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9849c-127">Example</span></span>  

<span data-ttu-id="9849c-128">O exemplo a seguir desabilita a espera de rotação em seções críticas quando contendeda.</span><span class="sxs-lookup"><span data-stu-id="9849c-128">The following example disables spin-waiting in critical sections when contended.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <Crst_DisableSpinWait enabled="1"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9849c-129">Confira também</span><span class="sxs-lookup"><span data-stu-id="9849c-129">See also</span></span>

- [<span data-ttu-id="9849c-130">Esquema de configurações do runtime</span><span class="sxs-lookup"><span data-stu-id="9849c-130">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="9849c-131">Esquema do arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="9849c-131">Configuration File Schema</span></span>](../index.md)
