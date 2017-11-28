---
title: "&lt;configuração&gt; elemento"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration
helpviewer_keywords:
- <configuration> element
- configuration element
- container tags, <configuration> element
ms.assetid: 2ec1c9dc-2e5c-4ef0-9958-81670ab88449
caps.latest.revision: "15"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 2241f3e835defe308b94d0cbad96020518dfd19b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="configuration-element"></a><span data-ttu-id="ed98d-102">\<Configuração > elemento</span><span class="sxs-lookup"><span data-stu-id="ed98d-102">\<configuration> element</span></span>

<span data-ttu-id="ed98d-103">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ed98d-103">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>

<span data-ttu-id="ed98d-104">**\<configuration>**</span><span class="sxs-lookup"><span data-stu-id="ed98d-104">**\<configuration>**</span></span>

## <a name="syntax"></a><span data-ttu-id="ed98d-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ed98d-105">Syntax</span></span>

```xml
<configuration>
  <!-- Configuration settings -->
</configuration>
```

## <a name="attributes"></a><span data-ttu-id="ed98d-106">Atributos</span><span class="sxs-lookup"><span data-stu-id="ed98d-106">Attributes</span></span>

<span data-ttu-id="ed98d-107">Nenhum</span><span class="sxs-lookup"><span data-stu-id="ed98d-107">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="ed98d-108">Elemento pai</span><span class="sxs-lookup"><span data-stu-id="ed98d-108">Parent element</span></span>

<span data-ttu-id="ed98d-109">Nenhum</span><span class="sxs-lookup"><span data-stu-id="ed98d-109">None</span></span>

## <a name="child-elements"></a><span data-ttu-id="ed98d-110">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ed98d-110">Child elements</span></span>

|     | <span data-ttu-id="ed98d-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="ed98d-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="ed98d-112">**\<assemblyBinding >**</span><span class="sxs-lookup"><span data-stu-id="ed98d-112">**\<assemblyBinding>**</span></span>](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) | <span data-ttu-id="ed98d-113">Especifica a diretiva de ligação de assembly no nível de configuração.</span><span class="sxs-lookup"><span data-stu-id="ed98d-113">Specifies assembly binding policy at the configuration level.</span></span>|
| [<span data-ttu-id="ed98d-114">**\<inicialização >** esquema de configurações</span><span class="sxs-lookup"><span data-stu-id="ed98d-114">**\<startup>** Settings Schema</span></span>](~/docs/framework/configure-apps/file-schema/startup/index.md) | <span data-ttu-id="ed98d-115">Todos os elementos no esquema de configurações de inicialização.</span><span class="sxs-lookup"><span data-stu-id="ed98d-115">All elements in the startup settings schema.</span></span> |
| [<span data-ttu-id="ed98d-116">**\<tempo de execução >** esquema de configurações</span><span class="sxs-lookup"><span data-stu-id="ed98d-116">**\<runtime>** Settings Schema</span></span>](~/docs/framework/configure-apps/file-schema/runtime/index.md) | <span data-ttu-id="ed98d-117">Todos os elementos no esquema de configurações de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="ed98d-117">All elements in the runtime settings schema.</span></span> |
| [<span data-ttu-id="ed98d-118">**\<System.Runtime.Remoting >** esquema de configurações</span><span class="sxs-lookup"><span data-stu-id="ed98d-118">**\<system.runtime.remoting>** Settings Schema</span></span>](http://msdn.microsoft.com/dc2d1e62-9af7-4ca1-99fd-98b93bb4db9e) | <span data-ttu-id="ed98d-119">Todos os elementos no esquema de configurações de comunicação remota.</span><span class="sxs-lookup"><span data-stu-id="ed98d-119">All elements in the remoting settings schema.</span></span> |
| [<span data-ttu-id="ed98d-120">**\<system.Net >** esquema de configurações</span><span class="sxs-lookup"><span data-stu-id="ed98d-120">**\<system.Net>** Settings Schema</span></span>](~/docs/framework/configure-apps/file-schema/network/index.md) | <span data-ttu-id="ed98d-121">Todos os elementos no esquema de configurações de rede.</span><span class="sxs-lookup"><span data-stu-id="ed98d-121">All elements in the network settings schema.</span></span> |
| [<span data-ttu-id="ed98d-122">**\<cryptographySettings >** esquema de configurações</span><span class="sxs-lookup"><span data-stu-id="ed98d-122">**\<cryptographySettings>** Settings Schema</span></span>](~/docs/framework/configure-apps/file-schema/cryptography/index.md) | <span data-ttu-id="ed98d-123">Todos os elementos no esquema de configurações de criptografia.</span><span class="sxs-lookup"><span data-stu-id="ed98d-123">All elements in the crypto settings schema.</span></span> |
| [<span data-ttu-id="ed98d-124">**\<Configuração >** esquema de seções</span><span class="sxs-lookup"><span data-stu-id="ed98d-124">**\<configuration>** Sections Schema</span></span>](~/docs/framework/configure-apps/file-schema/configuration-sections-schema.md) | <span data-ttu-id="ed98d-125">Todos os elementos no esquema de configurações da seção de configuração.</span><span class="sxs-lookup"><span data-stu-id="ed98d-125">All elements in the configuration section settings schema.</span></span> |
| [<span data-ttu-id="ed98d-126">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="ed98d-126">Trace and Debug Settings Schema</span></span>](~/docs/framework/configure-apps/file-schema/trace-debug/index.md) | <span data-ttu-id="ed98d-127">Todos os elementos no esquema de configurações de rastreamento e depuração.</span><span class="sxs-lookup"><span data-stu-id="ed98d-127">All elements in the trace and debug settings schema.</span></span> |
| <span data-ttu-id="ed98d-128">[Esquema de configurações de configuração do ASP.NET](https://msdn.microsoft.com/library/b5ysx397(v=vs.100).aspx)</span><span class="sxs-lookup"><span data-stu-id="ed98d-128">[ASP.NET Configuration Settings Schema](https://msdn.microsoft.com/library/b5ysx397(v=vs.100).aspx)</span></span> | <span data-ttu-id="ed98d-129">Todos os elementos no esquema de configuração do ASP.NET, que inclui elementos para configurar sites e aplicativos Web do ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="ed98d-129">All elements in the ASP.NET configuration schema, which includes elements for configuring ASP.NET Web sites and applications.</span></span> <span data-ttu-id="ed98d-130">Usado em *Web. config* arquivos.</span><span class="sxs-lookup"><span data-stu-id="ed98d-130">Used in *Web.config* files.</span></span> |
| [<span data-ttu-id="ed98d-131">**\<webServices >** esquema de configurações</span><span class="sxs-lookup"><span data-stu-id="ed98d-131">**\<webServices>** Settings Schema</span></span>](http://msdn.microsoft.com/f84d6d55-1add-4eb7-ae46-33df5833ea2e) | <span data-ttu-id="ed98d-132">Todos os elementos no esquema de configurações de serviços Web.</span><span class="sxs-lookup"><span data-stu-id="ed98d-132">All elements in the Web services settings schema.</span></span> |
| [<span data-ttu-id="ed98d-133">Esquema de configurações Web</span><span class="sxs-lookup"><span data-stu-id="ed98d-133">Web Settings Schema</span></span>](~/docs/framework/configure-apps/file-schema/web/index.md) | <span data-ttu-id="ed98d-134">Todos os elementos do esquema de configurações da Web, que incluem elementos para configurar como o ASP.NET, funciona com um aplicativo host, como o IIS.</span><span class="sxs-lookup"><span data-stu-id="ed98d-134">All elements in the Web settings schema, which includes elements for configuring how ASP.NET works with a host application such as IIS.</span></span> <span data-ttu-id="ed98d-135">Usado em *ASPNET* arquivos.</span><span class="sxs-lookup"><span data-stu-id="ed98d-135">Used in *aspnet.config* files.</span></span> |

## <a name="remarks"></a><span data-ttu-id="ed98d-136">Comentários</span><span class="sxs-lookup"><span data-stu-id="ed98d-136">Remarks</span></span>

<span data-ttu-id="ed98d-137">Cada arquivo de configuração deve conter exatamente um  **\<Configuração >** elemento.</span><span class="sxs-lookup"><span data-stu-id="ed98d-137">Each configuration file must contain exactly one **\<configuration>** element.</span></span>

## <a name="see-also"></a><span data-ttu-id="ed98d-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ed98d-138">See also</span></span>

[<span data-ttu-id="ed98d-139">Esquema de arquivo de configuração para o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ed98d-139">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
