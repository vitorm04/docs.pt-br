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
ms.openlocfilehash: 40c0ab5f18d5aae2c99dd66747d3435f0826af8b
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47200315"
---
# <a name="configuration-element"></a><span data-ttu-id="f534a-102">\<Configuração > elemento</span><span class="sxs-lookup"><span data-stu-id="f534a-102">\<configuration> element</span></span>

<span data-ttu-id="f534a-103">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f534a-103">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>

<span data-ttu-id="f534a-104">**\<configuration>**</span><span class="sxs-lookup"><span data-stu-id="f534a-104">**\<configuration>**</span></span>

## <a name="syntax"></a><span data-ttu-id="f534a-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f534a-105">Syntax</span></span>

```xml
<configuration>
  <!-- Configuration settings -->
</configuration>
```

## <a name="attributes"></a><span data-ttu-id="f534a-106">Atributos</span><span class="sxs-lookup"><span data-stu-id="f534a-106">Attributes</span></span>

<span data-ttu-id="f534a-107">Nenhum</span><span class="sxs-lookup"><span data-stu-id="f534a-107">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="f534a-108">Elemento pai</span><span class="sxs-lookup"><span data-stu-id="f534a-108">Parent element</span></span>

<span data-ttu-id="f534a-109">Nenhum</span><span class="sxs-lookup"><span data-stu-id="f534a-109">None</span></span>

## <a name="child-elements"></a><span data-ttu-id="f534a-110">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f534a-110">Child elements</span></span>

|     | <span data-ttu-id="f534a-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="f534a-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="f534a-112">**\<assemblyBinding >**</span><span class="sxs-lookup"><span data-stu-id="f534a-112">**\<assemblyBinding>**</span></span>](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) | <span data-ttu-id="f534a-113">Especifica a diretiva de ligação de assembly no nível de configuração.</span><span class="sxs-lookup"><span data-stu-id="f534a-113">Specifies assembly binding policy at the configuration level.</span></span>|
| [<span data-ttu-id="f534a-114">**\<inicialização >** esquema de configurações</span><span class="sxs-lookup"><span data-stu-id="f534a-114">**\<startup>** Settings Schema</span></span>](~/docs/framework/configure-apps/file-schema/startup/index.md) | <span data-ttu-id="f534a-115">Todos os elementos no esquema de configurações de inicialização.</span><span class="sxs-lookup"><span data-stu-id="f534a-115">All elements in the startup settings schema.</span></span> |
| [<span data-ttu-id="f534a-116">**\<tempo de execução >** esquema de configurações</span><span class="sxs-lookup"><span data-stu-id="f534a-116">**\<runtime>** Settings Schema</span></span>](~/docs/framework/configure-apps/file-schema/runtime/index.md) | <span data-ttu-id="f534a-117">Todos os elementos no esquema de configurações de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="f534a-117">All elements in the runtime settings schema.</span></span> |
| [<span data-ttu-id="f534a-118">**\<Remoting >** esquema de configurações</span><span class="sxs-lookup"><span data-stu-id="f534a-118">**\<system.runtime.remoting>** Settings Schema</span></span>](https://msdn.microsoft.com/dc2d1e62-9af7-4ca1-99fd-98b93bb4db9e) | <span data-ttu-id="f534a-119">Todos os elementos no esquema de configurações de comunicação remota.</span><span class="sxs-lookup"><span data-stu-id="f534a-119">All elements in the remoting settings schema.</span></span> |
| [<span data-ttu-id="f534a-120">**\<system.Net >** esquema de configurações</span><span class="sxs-lookup"><span data-stu-id="f534a-120">**\<system.Net>** Settings Schema</span></span>](~/docs/framework/configure-apps/file-schema/network/index.md) | <span data-ttu-id="f534a-121">Todos os elementos no esquema de configurações de rede.</span><span class="sxs-lookup"><span data-stu-id="f534a-121">All elements in the network settings schema.</span></span> |
| [<span data-ttu-id="f534a-122">**\<cryptographySettings >** esquema de configurações</span><span class="sxs-lookup"><span data-stu-id="f534a-122">**\<cryptographySettings>** Settings Schema</span></span>](~/docs/framework/configure-apps/file-schema/cryptography/index.md) | <span data-ttu-id="f534a-123">Todos os elementos no esquema de configurações de criptografia.</span><span class="sxs-lookup"><span data-stu-id="f534a-123">All elements in the crypto settings schema.</span></span> |
| [<span data-ttu-id="f534a-124">**\<Configuração >** esquema de seções</span><span class="sxs-lookup"><span data-stu-id="f534a-124">**\<configuration>** Sections Schema</span></span>](~/docs/framework/configure-apps/file-schema/configuration-sections-schema.md) | <span data-ttu-id="f534a-125">Todos os elementos no esquema de configurações da seção de configuração.</span><span class="sxs-lookup"><span data-stu-id="f534a-125">All elements in the configuration section settings schema.</span></span> |
| [<span data-ttu-id="f534a-126">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="f534a-126">Trace and Debug Settings Schema</span></span>](~/docs/framework/configure-apps/file-schema/trace-debug/index.md) | <span data-ttu-id="f534a-127">Todos os elementos no esquema de configurações de rastreamento e depuração.</span><span class="sxs-lookup"><span data-stu-id="f534a-127">All elements in the trace and debug settings schema.</span></span> |
| <span data-ttu-id="f534a-128">[Esquema de configurações de configuração do ASP.NET](https://msdn.microsoft.com/library/b5ysx397(v=vs.100).aspx)</span><span class="sxs-lookup"><span data-stu-id="f534a-128">[ASP.NET Configuration Settings Schema](https://msdn.microsoft.com/library/b5ysx397(v=vs.100).aspx)</span></span> | <span data-ttu-id="f534a-129">Todos os elementos no esquema de configuração de ASP.NET, que inclui elementos para configurar sites e aplicativos Web do ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="f534a-129">All elements in the ASP.NET configuration schema, which includes elements for configuring ASP.NET Web sites and applications.</span></span> <span data-ttu-id="f534a-130">Usado na *Web. config* arquivos.</span><span class="sxs-lookup"><span data-stu-id="f534a-130">Used in *Web.config* files.</span></span> |
| [<span data-ttu-id="f534a-131">**\<serviços Web >** esquema de configurações</span><span class="sxs-lookup"><span data-stu-id="f534a-131">**\<webServices>** Settings Schema</span></span>](https://msdn.microsoft.com/f84d6d55-1add-4eb7-ae46-33df5833ea2e) | <span data-ttu-id="f534a-132">Todos os elementos no esquema de configurações de serviços da Web.</span><span class="sxs-lookup"><span data-stu-id="f534a-132">All elements in the Web services settings schema.</span></span> |
| [<span data-ttu-id="f534a-133">Esquema de configurações Web</span><span class="sxs-lookup"><span data-stu-id="f534a-133">Web Settings Schema</span></span>](~/docs/framework/configure-apps/file-schema/web/index.md) | <span data-ttu-id="f534a-134">Todos os elementos do esquema de configurações da Web, que incluem elementos para configurar como o ASP.NET, funciona com um aplicativo host, como o IIS.</span><span class="sxs-lookup"><span data-stu-id="f534a-134">All elements in the Web settings schema, which includes elements for configuring how ASP.NET works with a host application such as IIS.</span></span> <span data-ttu-id="f534a-135">Usado na *ASPNET* arquivos.</span><span class="sxs-lookup"><span data-stu-id="f534a-135">Used in *aspnet.config* files.</span></span> |

## <a name="remarks"></a><span data-ttu-id="f534a-136">Comentários</span><span class="sxs-lookup"><span data-stu-id="f534a-136">Remarks</span></span>

<span data-ttu-id="f534a-137">Cada arquivo de configuração deve conter exatamente um  **\<configuration >** elemento.</span><span class="sxs-lookup"><span data-stu-id="f534a-137">Each configuration file must contain exactly one **\<configuration>** element.</span></span>

## <a name="see-also"></a><span data-ttu-id="f534a-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f534a-138">See also</span></span>

[<span data-ttu-id="f534a-139">Esquema de arquivo de configuração para o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f534a-139">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
