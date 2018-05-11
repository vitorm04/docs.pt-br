---
title: '&lt;configuração&gt; elemento'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration
helpviewer_keywords:
- <configuration> element
- configuration element
- container tags, <configuration> element
ms.assetid: 2ec1c9dc-2e5c-4ef0-9958-81670ab88449
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 2d75b25734b92df062d3dc46824da44883ab46d5
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="configuration-element"></a><span data-ttu-id="3895b-102">\<Configuração > elemento</span><span class="sxs-lookup"><span data-stu-id="3895b-102">\<configuration> element</span></span>

<span data-ttu-id="3895b-103">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3895b-103">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>

<span data-ttu-id="3895b-104">**\<configuration>**</span><span class="sxs-lookup"><span data-stu-id="3895b-104">**\<configuration>**</span></span>

## <a name="syntax"></a><span data-ttu-id="3895b-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3895b-105">Syntax</span></span>

```xml
<configuration>
  <!-- Configuration settings -->
</configuration>
```

## <a name="attributes"></a><span data-ttu-id="3895b-106">Atributos</span><span class="sxs-lookup"><span data-stu-id="3895b-106">Attributes</span></span>

<span data-ttu-id="3895b-107">Nenhum</span><span class="sxs-lookup"><span data-stu-id="3895b-107">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="3895b-108">Elemento pai</span><span class="sxs-lookup"><span data-stu-id="3895b-108">Parent element</span></span>

<span data-ttu-id="3895b-109">Nenhum</span><span class="sxs-lookup"><span data-stu-id="3895b-109">None</span></span>

## <a name="child-elements"></a><span data-ttu-id="3895b-110">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="3895b-110">Child elements</span></span>

|     | <span data-ttu-id="3895b-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="3895b-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="3895b-112">**\<assemblyBinding >**</span><span class="sxs-lookup"><span data-stu-id="3895b-112">**\<assemblyBinding>**</span></span>](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) | <span data-ttu-id="3895b-113">Especifica a diretiva de ligação de assembly no nível de configuração.</span><span class="sxs-lookup"><span data-stu-id="3895b-113">Specifies assembly binding policy at the configuration level.</span></span>|
| [<span data-ttu-id="3895b-114">**\<inicialização >** esquema de configurações</span><span class="sxs-lookup"><span data-stu-id="3895b-114">**\<startup>** Settings Schema</span></span>](~/docs/framework/configure-apps/file-schema/startup/index.md) | <span data-ttu-id="3895b-115">Todos os elementos no esquema de configurações de inicialização.</span><span class="sxs-lookup"><span data-stu-id="3895b-115">All elements in the startup settings schema.</span></span> |
| [<span data-ttu-id="3895b-116">**\<tempo de execução >** esquema de configurações</span><span class="sxs-lookup"><span data-stu-id="3895b-116">**\<runtime>** Settings Schema</span></span>](~/docs/framework/configure-apps/file-schema/runtime/index.md) | <span data-ttu-id="3895b-117">Todos os elementos no esquema de configurações de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="3895b-117">All elements in the runtime settings schema.</span></span> |
| [<span data-ttu-id="3895b-118">**\<System.Runtime.Remoting >** esquema de configurações</span><span class="sxs-lookup"><span data-stu-id="3895b-118">**\<system.runtime.remoting>** Settings Schema</span></span>](http://msdn.microsoft.com/dc2d1e62-9af7-4ca1-99fd-98b93bb4db9e) | <span data-ttu-id="3895b-119">Todos os elementos no esquema de configurações de comunicação remota.</span><span class="sxs-lookup"><span data-stu-id="3895b-119">All elements in the remoting settings schema.</span></span> |
| [<span data-ttu-id="3895b-120">**\<system.Net >** esquema de configurações</span><span class="sxs-lookup"><span data-stu-id="3895b-120">**\<system.Net>** Settings Schema</span></span>](~/docs/framework/configure-apps/file-schema/network/index.md) | <span data-ttu-id="3895b-121">Todos os elementos no esquema de configurações de rede.</span><span class="sxs-lookup"><span data-stu-id="3895b-121">All elements in the network settings schema.</span></span> |
| [<span data-ttu-id="3895b-122">**\<cryptographySettings >** esquema de configurações</span><span class="sxs-lookup"><span data-stu-id="3895b-122">**\<cryptographySettings>** Settings Schema</span></span>](~/docs/framework/configure-apps/file-schema/cryptography/index.md) | <span data-ttu-id="3895b-123">Todos os elementos no esquema de configurações de criptografia.</span><span class="sxs-lookup"><span data-stu-id="3895b-123">All elements in the crypto settings schema.</span></span> |
| [<span data-ttu-id="3895b-124">**\<Configuração >** esquema de seções</span><span class="sxs-lookup"><span data-stu-id="3895b-124">**\<configuration>** Sections Schema</span></span>](~/docs/framework/configure-apps/file-schema/configuration-sections-schema.md) | <span data-ttu-id="3895b-125">Todos os elementos no esquema de configurações da seção de configuração.</span><span class="sxs-lookup"><span data-stu-id="3895b-125">All elements in the configuration section settings schema.</span></span> |
| [<span data-ttu-id="3895b-126">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="3895b-126">Trace and Debug Settings Schema</span></span>](~/docs/framework/configure-apps/file-schema/trace-debug/index.md) | <span data-ttu-id="3895b-127">Todos os elementos no esquema de configurações de rastreamento e depuração.</span><span class="sxs-lookup"><span data-stu-id="3895b-127">All elements in the trace and debug settings schema.</span></span> |
| <span data-ttu-id="3895b-128">[Esquema de configurações de configuração do ASP.NET](https://msdn.microsoft.com/library/b5ysx397(v=vs.100).aspx)</span><span class="sxs-lookup"><span data-stu-id="3895b-128">[ASP.NET Configuration Settings Schema](https://msdn.microsoft.com/library/b5ysx397(v=vs.100).aspx)</span></span> | <span data-ttu-id="3895b-129">Todos os elementos no esquema de configuração do ASP.NET, que inclui elementos para configurar sites e aplicativos Web do ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="3895b-129">All elements in the ASP.NET configuration schema, which includes elements for configuring ASP.NET Web sites and applications.</span></span> <span data-ttu-id="3895b-130">Usado em *Web. config* arquivos.</span><span class="sxs-lookup"><span data-stu-id="3895b-130">Used in *Web.config* files.</span></span> |
| [<span data-ttu-id="3895b-131">**\<webServices >** esquema de configurações</span><span class="sxs-lookup"><span data-stu-id="3895b-131">**\<webServices>** Settings Schema</span></span>](http://msdn.microsoft.com/f84d6d55-1add-4eb7-ae46-33df5833ea2e) | <span data-ttu-id="3895b-132">Todos os elementos no esquema de configurações de serviços Web.</span><span class="sxs-lookup"><span data-stu-id="3895b-132">All elements in the Web services settings schema.</span></span> |
| [<span data-ttu-id="3895b-133">Esquema de configurações Web</span><span class="sxs-lookup"><span data-stu-id="3895b-133">Web Settings Schema</span></span>](~/docs/framework/configure-apps/file-schema/web/index.md) | <span data-ttu-id="3895b-134">Todos os elementos do esquema de configurações da Web, que incluem elementos para configurar como o ASP.NET, funciona com um aplicativo host, como o IIS.</span><span class="sxs-lookup"><span data-stu-id="3895b-134">All elements in the Web settings schema, which includes elements for configuring how ASP.NET works with a host application such as IIS.</span></span> <span data-ttu-id="3895b-135">Usado em *ASPNET* arquivos.</span><span class="sxs-lookup"><span data-stu-id="3895b-135">Used in *aspnet.config* files.</span></span> |

## <a name="remarks"></a><span data-ttu-id="3895b-136">Comentários</span><span class="sxs-lookup"><span data-stu-id="3895b-136">Remarks</span></span>

<span data-ttu-id="3895b-137">Cada arquivo de configuração deve conter exatamente um  **\<Configuração >** elemento.</span><span class="sxs-lookup"><span data-stu-id="3895b-137">Each configuration file must contain exactly one **\<configuration>** element.</span></span>

## <a name="see-also"></a><span data-ttu-id="3895b-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3895b-138">See also</span></span>

[<span data-ttu-id="3895b-139">Esquema de arquivo de configuração para o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="3895b-139">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
