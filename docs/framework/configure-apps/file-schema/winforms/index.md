---
title: Seção de configuração do Windows Forms
ms.date: 04/07/2017
ms.assetid: 6eb142d5-fc98-40e2-9d90-84733f2a27ba
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bbb2c4157ba702182056c98c959a60569e8c3d1e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61786406"
---
# <a name="windows-forms-configuration-section"></a><span data-ttu-id="399ae-102">Seção de configuração do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="399ae-102">Windows Forms Configuration Section</span></span>
<span data-ttu-id="399ae-103">As definições de configuração do Windows Forms permitem que um aplicativo do Windows Forms armazene e recupere informações sobre configurações personalizadas de aplicativo, como suporte a vários monitores, suporte ao DPI e outras configurações predefinidas.</span><span class="sxs-lookup"><span data-stu-id="399ae-103">Windows Forms configuration settings allow a Windows Forms app to store and retrieve information about customized application settings such as multi-monitor support, high DPI support, and other predefined configuration settings.</span></span>

<span data-ttu-id="399ae-104">As definições de configuração de aplicativo do Windows Forms são armazenadas em um elemento `System.Windows.Forms.ApplicationConfigurationSection` do arquivo de configuração de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="399ae-104">Windows Forms application configuration settings are stored in an application configuration file's `System.Windows.Forms.ApplicationConfigurationSection` element.</span></span>

## <a name="syntax"></a><span data-ttu-id="399ae-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="399ae-105">Syntax</span></span>

```xml
<configuration>
  <System.Windows.Forms.ApplicationConfigurationSection>
  ...
  </System.Windows.Forms.ApplicationConfigurationSection>
</configuration>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="399ae-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="399ae-106">Attributes and elements</span></span>

<span data-ttu-id="399ae-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="399ae-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="399ae-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="399ae-108">Attributes</span></span>

<span data-ttu-id="399ae-109">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="399ae-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="399ae-110">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="399ae-110">Child elements</span></span>

<span data-ttu-id="399ae-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="399ae-111">Element</span></span>  |<span data-ttu-id="399ae-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="399ae-112">Description</span></span> |
---------|---------|
[`<add>`](../../../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md) | <span data-ttu-id="399ae-113">Adiciona uma chave de definição de configuração com um valor especificado</span><span class="sxs-lookup"><span data-stu-id="399ae-113">Adds a configuration setting key with a specified value</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="399ae-114">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="399ae-114">Parent elements</span></span>

<span data-ttu-id="399ae-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="399ae-115">Element</span></span>  |<span data-ttu-id="399ae-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="399ae-116">Description</span></span> |
---------|---------|
[<span data-ttu-id="399ae-117">\<configuration></span><span class="sxs-lookup"><span data-stu-id="399ae-117">\<configuration></span></span>](../configuration-element.md) | <span data-ttu-id="399ae-118">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e Windows Forms</span><span class="sxs-lookup"><span data-stu-id="399ae-118">The root element in every configuration file used by the common language runtime and Windows Forms applications</span></span> |

## <a name="remarks"></a><span data-ttu-id="399ae-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="399ae-119">Remarks</span></span>

<span data-ttu-id="399ae-120">A partir do .NET Framework 4.7, o elemento `<System.Windows.Forms.ApplicationConfigurationSection>` permite configurar os aplicativos do Windows Forms para aproveitar os recursos adicionados em versões recentes do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="399ae-120">Starting with the .NET Framework 4.7, the `<System.Windows.Forms.ApplicationConfigurationSection>` element allows you to configure Windows Forms applications to take advantage of features added in recent releases of the .NET Framework.</span></span> 

<span data-ttu-id="399ae-121">O elemento `<System.Windows.Forms.ApplicationConfigurationSection>` pode incluir um ou mais elementos [`<add>`](../../../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md) filho e cada um deles define uma definição de configuração específica.</span><span class="sxs-lookup"><span data-stu-id="399ae-121">The `<System.Windows.Forms.ApplicationConfigurationSection>` element can include one or more child [`<add>`](../../../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md) elements, each of which defines a specific configuration setting.</span></span>

## <a name="see-also"></a><span data-ttu-id="399ae-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="399ae-122">See also</span></span>

- [<span data-ttu-id="399ae-123">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="399ae-123">Configuration File Schema</span></span>](../index.md)
- <span data-ttu-id="399ae-124">[High DPI Support in Windows Forms](../../../../../docs/framework/winforms/high-dpi-support-in-windows-forms.md) (Suporte a alto DPI no Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="399ae-124">[High DPI Support in Windows Forms](../../../../../docs/framework/winforms/high-dpi-support-in-windows-forms.md)</span></span>
