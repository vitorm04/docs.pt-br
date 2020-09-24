---
title: Seção de configuração do Windows Forms
ms.date: 04/07/2017
ms.assetid: 6eb142d5-fc98-40e2-9d90-84733f2a27ba
ms.openlocfilehash: 2d518ec03602580f3c5d00ef2901ff7d7ac1d81b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148497"
---
# <a name="windows-forms-configuration-section"></a><span data-ttu-id="60881-102">Seção de configuração do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="60881-102">Windows Forms Configuration Section</span></span>

<span data-ttu-id="60881-103">As definições de configuração do Windows Forms permitem que um aplicativo do Windows Forms armazene e recupere informações sobre configurações personalizadas de aplicativo, como suporte a vários monitores, suporte ao DPI e outras configurações predefinidas.</span><span class="sxs-lookup"><span data-stu-id="60881-103">Windows Forms configuration settings allow a Windows Forms app to store and retrieve information about customized application settings such as multi-monitor support, high DPI support, and other predefined configuration settings.</span></span>

<span data-ttu-id="60881-104">As definições de configuração de aplicativo do Windows Forms são armazenadas em um elemento `System.Windows.Forms.ApplicationConfigurationSection` do arquivo de configuração de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="60881-104">Windows Forms application configuration settings are stored in an application configuration file's `System.Windows.Forms.ApplicationConfigurationSection` element.</span></span>

## <a name="syntax"></a><span data-ttu-id="60881-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="60881-105">Syntax</span></span>

```xml
<configuration>
  <System.Windows.Forms.ApplicationConfigurationSection>
  ...
  </System.Windows.Forms.ApplicationConfigurationSection>
</configuration>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="60881-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="60881-106">Attributes and elements</span></span>

<span data-ttu-id="60881-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="60881-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="60881-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="60881-108">Attributes</span></span>

<span data-ttu-id="60881-109">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="60881-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="60881-110">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="60881-110">Child elements</span></span>

<span data-ttu-id="60881-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="60881-111">Element</span></span>  |<span data-ttu-id="60881-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="60881-112">Description</span></span> |
---------|---------|
[`<add>`](windows-forms-add-configuration-element.md) | <span data-ttu-id="60881-113">Adiciona uma chave de definição de configuração com um valor especificado</span><span class="sxs-lookup"><span data-stu-id="60881-113">Adds a configuration setting key with a specified value</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="60881-114">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="60881-114">Parent elements</span></span>

<span data-ttu-id="60881-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="60881-115">Element</span></span>  |<span data-ttu-id="60881-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="60881-116">Description</span></span> |
---------|---------|
[\<configuration>](../configuration-element.md) | <span data-ttu-id="60881-117">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e Windows Forms</span><span class="sxs-lookup"><span data-stu-id="60881-117">The root element in every configuration file used by the common language runtime and Windows Forms applications</span></span> |

## <a name="remarks"></a><span data-ttu-id="60881-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="60881-118">Remarks</span></span>

<span data-ttu-id="60881-119">A partir do .NET Framework 4.7, o elemento `<System.Windows.Forms.ApplicationConfigurationSection>` permite configurar os aplicativos do Windows Forms para aproveitar os recursos adicionados em versões recentes do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="60881-119">Starting with the .NET Framework 4.7, the `<System.Windows.Forms.ApplicationConfigurationSection>` element allows you to configure Windows Forms applications to take advantage of features added in recent releases of the .NET Framework.</span></span>

<span data-ttu-id="60881-120">O `<System.Windows.Forms.ApplicationConfigurationSection>` elemento pode incluir um ou mais [`<add>`](windows-forms-add-configuration-element.md) elementos filho, cada um deles define uma definição de configuração específica.</span><span class="sxs-lookup"><span data-stu-id="60881-120">The `<System.Windows.Forms.ApplicationConfigurationSection>` element can include one or more child [`<add>`](windows-forms-add-configuration-element.md) elements, each of which defines a specific configuration setting.</span></span>

## <a name="see-also"></a><span data-ttu-id="60881-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="60881-121">See also</span></span>

- [<span data-ttu-id="60881-122">Esquema do arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="60881-122">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="60881-123">Suporte a alto DPI no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="60881-123">High DPI Support in Windows Forms</span></span>](/dotnet/desktop/winforms/high-dpi-support-in-windows-forms)
