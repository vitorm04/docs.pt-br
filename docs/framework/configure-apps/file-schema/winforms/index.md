---
title: Seção de configuração do Windows Forms
ms.custom: ''
ms.date: 04/07/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6eb142d5-fc98-40e2-9d90-84733f2a27ba
caps.latest.revision: 6
author: rpetrusha
ms.author: ronpet
ms.workload:
- dotnet
ms.openlocfilehash: f2d83f5dcf6fa93ceba4d670470bd768a2ee1f88
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="windows-forms-configuration-section"></a><span data-ttu-id="ed9de-102">Seção de configuração do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ed9de-102">Windows Forms Configuration Section</span></span>
<span data-ttu-id="ed9de-103">As definições de configuração do Windows Forms permitem que um aplicativo do Windows Forms armazene e recupere informações sobre configurações personalizadas de aplicativo, como suporte a vários monitores, suporte ao DPI e outras configurações predefinidas.</span><span class="sxs-lookup"><span data-stu-id="ed9de-103">Windows Forms configuration settings allow a Windows Forms app to store and retrieve information about customized application settings such as multi-monitor support, high DPI support, and other predefined configuration settings.</span></span>

<span data-ttu-id="ed9de-104">As definições de configuração de aplicativo do Windows Forms são armazenadas em um elemento `System.Windows.Forms.ApplicationConfigurationSection` do arquivo de configuração de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ed9de-104">Windows Forms application configuration settings are stored in an application configuration file's `System.Windows.Forms.ApplicationConfigurationSection` element.</span></span>

## <a name="syntax"></a><span data-ttu-id="ed9de-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ed9de-105">Syntax</span></span>

```xml
<configuration>
  <System.Windows.Forms.ApplicationConfigurationSection>
  ...
  </System.Windows.Forms.ApplicationConfigurationSection>
</configuration>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ed9de-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ed9de-106">Attributes and elements</span></span>

<span data-ttu-id="ed9de-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ed9de-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="ed9de-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="ed9de-108">Attributes</span></span>

<span data-ttu-id="ed9de-109">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="ed9de-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ed9de-110">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ed9de-110">Child elements</span></span>

<span data-ttu-id="ed9de-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="ed9de-111">Element</span></span>  |<span data-ttu-id="ed9de-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="ed9de-112">Description</span></span> |
---------|---------|
[`<add>`](../../../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md) | <span data-ttu-id="ed9de-113">Adiciona uma chave de definição de configuração com um valor especificado</span><span class="sxs-lookup"><span data-stu-id="ed9de-113">Adds a configuration setting key with a specified value</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="ed9de-114">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ed9de-114">Parent elements</span></span>

<span data-ttu-id="ed9de-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="ed9de-115">Element</span></span>  |<span data-ttu-id="ed9de-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="ed9de-116">Description</span></span> |
---------|---------|
[<span data-ttu-id="ed9de-117">\<configuration></span><span class="sxs-lookup"><span data-stu-id="ed9de-117">\<configuration></span></span>](../configuration-element.md) | <span data-ttu-id="ed9de-118">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ed9de-118">The root element in every configuration file used by the common language runtime and Windows Forms applications</span></span> |

## <a name="remarks"></a><span data-ttu-id="ed9de-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="ed9de-119">Remarks</span></span>

<span data-ttu-id="ed9de-120">A partir do .NET Framework 4.7, o elemento `<System.Windows.Forms.ApplicationConfigurationSection>` permite configurar os aplicativos do Windows Forms para aproveitar os recursos adicionados em versões recentes do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ed9de-120">Starting with the .NET Framework 4.7, the `<System.Windows.Forms.ApplicationConfigurationSection>` element allows you to configure Windows Forms applications to take advantage of features added in recent releases of the .NET Framework.</span></span> 

<span data-ttu-id="ed9de-121">O elemento `<System.Windows.Forms.ApplicationConfigurationSection>` pode incluir um ou mais elementos [`<add>`](../../../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md) filho e cada um deles define uma definição de configuração específica.</span><span class="sxs-lookup"><span data-stu-id="ed9de-121">The `<System.Windows.Forms.ApplicationConfigurationSection>` element can include one or more child [`<add>`](../../../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md) elements, each of which defines a specific configuration setting.</span></span>

## <a name="see-also"></a><span data-ttu-id="ed9de-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ed9de-122">See also</span></span>

<span data-ttu-id="ed9de-123">[Esquema de arquivo de configuração](../index.md) </span><span class="sxs-lookup"><span data-stu-id="ed9de-123">[Configuration File Schema](../index.md) </span></span>  
<span data-ttu-id="ed9de-124">[High DPI Support in Windows Forms](../../../../../docs/framework/winforms/high-dpi-support-in-windows-forms.md) (Suporte a alto DPI no Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="ed9de-124">[High DPI Support in Windows Forms](../../../../../docs/framework/winforms/high-dpi-support-in-windows-forms.md)</span></span>
