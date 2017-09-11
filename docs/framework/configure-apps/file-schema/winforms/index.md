---
title: "Seção de configuração do Windows Forms | Microsoft Docs"
ms.custom: 
ms.date: 04/07/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6eb142d5-fc98-40e2-9d90-84733f2a27ba
caps.latest.revision: 6
author: rpetrusha
ms.author: ronpet
ms.translationtype: Human Translation
ms.sourcegitcommit: 39e8e757a446b30ab18914465853138e1c239e40
ms.openlocfilehash: dedf9497a684c4b11f84b60de21ec73b563c6d19
ms.contentlocale: pt-br
ms.lasthandoff: 05/03/2017

---
# <a name="windows-forms-configuration-section"></a><span data-ttu-id="2c4a7-102">Seção de configuração do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2c4a7-102">Windows Forms Configuration Section</span></span>
<span data-ttu-id="2c4a7-103">As definições de configuração do Windows Forms permitem que um aplicativo do Windows Forms armazene e recupere informações sobre configurações personalizadas de aplicativo, como suporte a vários monitores, suporte ao DPI e outras configurações predefinidas.</span><span class="sxs-lookup"><span data-stu-id="2c4a7-103">Windows Forms configuration settings allow a Windows Forms app to store and retrieve information about customized application settings such as multi-monitor support, high DPI support, and other predefined configuration settings.</span></span>

<span data-ttu-id="2c4a7-104">As definições de configuração de aplicativo do Windows Forms são armazenadas em um elemento `System.Windows.Forms.ConfigurationSection` do arquivo de configuração de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2c4a7-104">Windows Forms application configuration settings are stored in an application configuration file's `System.Windows.Forms.ConfigurationSection` element.</span></span>

## <a name="syntax"></a><span data-ttu-id="2c4a7-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2c4a7-105">Syntax</span></span>

```xml
<configuration>
  \<System.Windows.Forms.ConfigurationSection>
  ...
  \</System.Windows.Forms.ConfigurationSection>
</configuration>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2c4a7-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="2c4a7-106">Attributes and elements</span></span>

<span data-ttu-id="2c4a7-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="2c4a7-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="2c4a7-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="2c4a7-108">Attributes</span></span>

<span data-ttu-id="2c4a7-109">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="2c4a7-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2c4a7-110">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="2c4a7-110">Child elements</span></span>

<span data-ttu-id="2c4a7-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="2c4a7-111">Element</span></span>  |<span data-ttu-id="2c4a7-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="2c4a7-112">Description</span></span> |
---------|---------|
[`<add>`](../../../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md) | <span data-ttu-id="2c4a7-113">Adiciona uma chave de definição de configuração com um valor especificado</span><span class="sxs-lookup"><span data-stu-id="2c4a7-113">Adds a configuration setting key with a specified value</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="2c4a7-114">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="2c4a7-114">Parent elements</span></span>

<span data-ttu-id="2c4a7-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="2c4a7-115">Element</span></span>  |<span data-ttu-id="2c4a7-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="2c4a7-116">Description</span></span> |
---------|---------|
[<span data-ttu-id="2c4a7-117">\<configuration></span><span class="sxs-lookup"><span data-stu-id="2c4a7-117">\<configuration></span></span>](../configuration-element.md) | <span data-ttu-id="2c4a7-118">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2c4a7-118">The root element in every configuration file used by the common language runtime and Windows Forms applications</span></span> |

## <a name="remarks"></a><span data-ttu-id="2c4a7-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="2c4a7-119">Remarks</span></span>

<span data-ttu-id="2c4a7-120">A partir do .NET Framework 4.7, o elemento `<System.Windows.Forms.ConfigurationSection>` permite configurar os aplicativos do Windows Forms para aproveitar os recursos adicionados em versões recentes do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2c4a7-120">Starting with the .NET Framework 4.7, the `<System.Windows.Forms.ConfigurationSection>` element allows you to configure Windows Forms applications to take advantage of features added in recent releases of the .NET Framework.</span></span> 

<span data-ttu-id="2c4a7-121">O elemento `<System.Windows.Forms.ConfigurationSection>` pode incluir um ou mais elementos [`<add>`](../../../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md) filho e cada um deles define uma definição de configuração específica.</span><span class="sxs-lookup"><span data-stu-id="2c4a7-121">The `<System.Windows.Forms.ConfigurationSection>` element can include one or more child [`<add>`](../../../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md) elements, each of which defines a specific configuration setting.</span></span>

## <a name="see-also"></a><span data-ttu-id="2c4a7-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2c4a7-122">See also</span></span>

<span data-ttu-id="2c4a7-123">[Esquema de arquivo de configuração](../index.md)
[Suporte ao DPI alto no Windows Forms](../../../../../docs/framework/winforms/high-dpi-support-in-windows-forms.md)</span><span class="sxs-lookup"><span data-stu-id="2c4a7-123">[Configuration File Schema](../index.md)
[High DPI Support in Windows Forms](../../../../../docs/framework/winforms/high-dpi-support-in-windows-forms.md)</span></span>

