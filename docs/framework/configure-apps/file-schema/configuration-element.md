---
title: Elemento <configuration>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration
helpviewer_keywords:
- <configuration> element
- configuration element
- container tags, <configuration> element
ms.assetid: 2ec1c9dc-2e5c-4ef0-9958-81670ab88449
ms.openlocfilehash: 9a7b25c74763c020c0e19c3f6099db9001acf773
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705409"
---
# <a name="configuration-element"></a><span data-ttu-id="e4c32-102">\<Configuração > elemento</span><span class="sxs-lookup"><span data-stu-id="e4c32-102">\<configuration> element</span></span>

<span data-ttu-id="e4c32-103">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e4c32-103">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>

<span data-ttu-id="e4c32-104">**\<configuration>**</span><span class="sxs-lookup"><span data-stu-id="e4c32-104">**\<configuration>**</span></span>

## <a name="syntax"></a><span data-ttu-id="e4c32-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e4c32-105">Syntax</span></span>

```xml
<configuration>
  <!-- Configuration settings -->
</configuration>
```

## <a name="attributes"></a><span data-ttu-id="e4c32-106">Atributos</span><span class="sxs-lookup"><span data-stu-id="e4c32-106">Attributes</span></span>

<span data-ttu-id="e4c32-107">Nenhum</span><span class="sxs-lookup"><span data-stu-id="e4c32-107">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="e4c32-108">Elemento pai</span><span class="sxs-lookup"><span data-stu-id="e4c32-108">Parent element</span></span>

<span data-ttu-id="e4c32-109">Nenhum</span><span class="sxs-lookup"><span data-stu-id="e4c32-109">None</span></span>

## <a name="child-elements"></a><span data-ttu-id="e4c32-110">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="e4c32-110">Child elements</span></span>

|     | <span data-ttu-id="e4c32-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="e4c32-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="e4c32-112">**\<assemblyBinding>**</span><span class="sxs-lookup"><span data-stu-id="e4c32-112">**\<assemblyBinding>**</span></span>](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) | <span data-ttu-id="e4c32-113">Especifica a diretiva de ligação de assembly no nível de configuração.</span><span class="sxs-lookup"><span data-stu-id="e4c32-113">Specifies assembly binding policy at the configuration level.</span></span>|
| [<span data-ttu-id="e4c32-114">**\<inicialização >** esquema de configurações</span><span class="sxs-lookup"><span data-stu-id="e4c32-114">**\<startup>** Settings Schema</span></span>](~/docs/framework/configure-apps/file-schema/startup/index.md) | <span data-ttu-id="e4c32-115">Todos os elementos no esquema de configurações de inicialização.</span><span class="sxs-lookup"><span data-stu-id="e4c32-115">All elements in the startup settings schema.</span></span> |
| [<span data-ttu-id="e4c32-116">**\<tempo de execução >** esquema de configurações</span><span class="sxs-lookup"><span data-stu-id="e4c32-116">**\<runtime>** Settings Schema</span></span>](~/docs/framework/configure-apps/file-schema/runtime/index.md) | <span data-ttu-id="e4c32-117">Todos os elementos no esquema de configurações de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="e4c32-117">All elements in the runtime settings schema.</span></span> |
| <span data-ttu-id="e4c32-118">[**\<system.runtime.remoting>** Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e4c32-118">[**\<system.runtime.remoting>** Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100))</span></span> | <span data-ttu-id="e4c32-119">Todos os elementos no esquema de configurações de comunicação remota.</span><span class="sxs-lookup"><span data-stu-id="e4c32-119">All elements in the remoting settings schema.</span></span> |
| [<span data-ttu-id="e4c32-120">**\<system.Net>** Settings Schema</span><span class="sxs-lookup"><span data-stu-id="e4c32-120">**\<system.Net>** Settings Schema</span></span>](~/docs/framework/configure-apps/file-schema/network/index.md) | <span data-ttu-id="e4c32-121">Todos os elementos no esquema de configurações de rede.</span><span class="sxs-lookup"><span data-stu-id="e4c32-121">All elements in the network settings schema.</span></span> |
| [<span data-ttu-id="e4c32-122">**\<cryptographySettings>** Settings Schema</span><span class="sxs-lookup"><span data-stu-id="e4c32-122">**\<cryptographySettings>** Settings Schema</span></span>](~/docs/framework/configure-apps/file-schema/cryptography/index.md) | <span data-ttu-id="e4c32-123">Todos os elementos no esquema de configurações de criptografia.</span><span class="sxs-lookup"><span data-stu-id="e4c32-123">All elements in the crypto settings schema.</span></span> |
| [<span data-ttu-id="e4c32-124">**\<Configuração >** esquema de seções</span><span class="sxs-lookup"><span data-stu-id="e4c32-124">**\<configuration>** Sections Schema</span></span>](~/docs/framework/configure-apps/file-schema/configuration-sections-schema.md) | <span data-ttu-id="e4c32-125">Todos os elementos no esquema de configurações da seção de configuração.</span><span class="sxs-lookup"><span data-stu-id="e4c32-125">All elements in the configuration section settings schema.</span></span> |
| [<span data-ttu-id="e4c32-126">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="e4c32-126">Trace and Debug Settings Schema</span></span>](~/docs/framework/configure-apps/file-schema/trace-debug/index.md) | <span data-ttu-id="e4c32-127">Todos os elementos no esquema de configurações de rastreamento e depuração.</span><span class="sxs-lookup"><span data-stu-id="e4c32-127">All elements in the trace and debug settings schema.</span></span> |
| <span data-ttu-id="e4c32-128">[Esquema de configurações de configuração do ASP.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e4c32-128">[ASP.NET Configuration Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100))</span></span> | <span data-ttu-id="e4c32-129">Todos os elementos no esquema de configuração de ASP.NET, que inclui elementos para configurar sites e aplicativos Web do ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="e4c32-129">All elements in the ASP.NET configuration schema, which includes elements for configuring ASP.NET Web sites and applications.</span></span> <span data-ttu-id="e4c32-130">Usado na *Web. config* arquivos.</span><span class="sxs-lookup"><span data-stu-id="e4c32-130">Used in *Web.config* files.</span></span> |
| <span data-ttu-id="e4c32-131">[**\<webServices>** Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e4c32-131">[**\<webServices>** Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100))</span></span> | <span data-ttu-id="e4c32-132">Todos os elementos no esquema de configurações de serviços da Web.</span><span class="sxs-lookup"><span data-stu-id="e4c32-132">All elements in the Web services settings schema.</span></span> |
| [<span data-ttu-id="e4c32-133">Esquema de configurações Web</span><span class="sxs-lookup"><span data-stu-id="e4c32-133">Web Settings Schema</span></span>](~/docs/framework/configure-apps/file-schema/web/index.md) | <span data-ttu-id="e4c32-134">Todos os elementos do esquema de configurações da Web, que incluem elementos para configurar como o ASP.NET, funciona com um aplicativo host, como o IIS.</span><span class="sxs-lookup"><span data-stu-id="e4c32-134">All elements in the Web settings schema, which includes elements for configuring how ASP.NET works with a host application such as IIS.</span></span> <span data-ttu-id="e4c32-135">Usado na *ASPNET* arquivos.</span><span class="sxs-lookup"><span data-stu-id="e4c32-135">Used in *aspnet.config* files.</span></span> |

## <a name="remarks"></a><span data-ttu-id="e4c32-136">Comentários</span><span class="sxs-lookup"><span data-stu-id="e4c32-136">Remarks</span></span>

<span data-ttu-id="e4c32-137">Cada arquivo de configuração deve conter exatamente um  **\<configuration >** elemento.</span><span class="sxs-lookup"><span data-stu-id="e4c32-137">Each configuration file must contain exactly one **\<configuration>** element.</span></span>

## <a name="see-also"></a><span data-ttu-id="e4c32-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e4c32-138">See also</span></span>

- [<span data-ttu-id="e4c32-139">Esquema de arquivo de configuração para o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="e4c32-139">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
