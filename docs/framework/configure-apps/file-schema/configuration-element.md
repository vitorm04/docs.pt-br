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
ms.openlocfilehash: 8f79981a55d0bc9b1cd522e45f5606fda102c72c
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90544682"
---
# <a name="configuration-element"></a><span data-ttu-id="6e9f4-102">Elemento \<configuration></span><span class="sxs-lookup"><span data-stu-id="6e9f4-102">\<configuration> element</span></span>

<span data-ttu-id="6e9f4-103">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6e9f4-103">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>

**\<configuration>**

## <a name="syntax"></a><span data-ttu-id="6e9f4-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="6e9f4-104">Syntax</span></span>

```xml
<configuration>
  <!-- Configuration settings -->
</configuration>
```

## <a name="attributes"></a><span data-ttu-id="6e9f4-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="6e9f4-105">Attributes</span></span>

<span data-ttu-id="6e9f4-106">Nenhum</span><span class="sxs-lookup"><span data-stu-id="6e9f4-106">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="6e9f4-107">Elemento pai</span><span class="sxs-lookup"><span data-stu-id="6e9f4-107">Parent element</span></span>

<span data-ttu-id="6e9f4-108">Nenhum</span><span class="sxs-lookup"><span data-stu-id="6e9f4-108">None</span></span>

## <a name="child-elements"></a><span data-ttu-id="6e9f4-109">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="6e9f4-109">Child elements</span></span>

|     | <span data-ttu-id="6e9f4-110">Description</span><span class="sxs-lookup"><span data-stu-id="6e9f4-110">Description</span></span> |
| --- | ----------- |
| [**\<assemblyBinding>**](assemblybinding-element-for-configuration.md) | <span data-ttu-id="6e9f4-111">Especifica a diretiva de ligação de assembly no nível de configuração.</span><span class="sxs-lookup"><span data-stu-id="6e9f4-111">Specifies assembly binding policy at the configuration level.</span></span>|
| [<span data-ttu-id="6e9f4-112">**\<startup>** Esquema de configurações</span><span class="sxs-lookup"><span data-stu-id="6e9f4-112">**\<startup>** Settings Schema</span></span>](./startup/index.md) | <span data-ttu-id="6e9f4-113">Todos os elementos no esquema de configurações de inicialização.</span><span class="sxs-lookup"><span data-stu-id="6e9f4-113">All elements in the startup settings schema.</span></span> |
| [<span data-ttu-id="6e9f4-114">**\<runtime>** Esquema de configurações</span><span class="sxs-lookup"><span data-stu-id="6e9f4-114">**\<runtime>** Settings Schema</span></span>](./runtime/index.md) | <span data-ttu-id="6e9f4-115">Todos os elementos no esquema de configurações de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="6e9f4-115">All elements in the runtime settings schema.</span></span> |
| <span data-ttu-id="6e9f4-116">[**\<system.runtime.remoting>** Esquema de configurações](/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="6e9f4-116">[**\<system.runtime.remoting>** Settings Schema](/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100))</span></span> | <span data-ttu-id="6e9f4-117">Todos os elementos no esquema de configurações de comunicação remota.</span><span class="sxs-lookup"><span data-stu-id="6e9f4-117">All elements in the remoting settings schema.</span></span> |
| [<span data-ttu-id="6e9f4-118">**\<system.Net>** Esquema de configurações</span><span class="sxs-lookup"><span data-stu-id="6e9f4-118">**\<system.Net>** Settings Schema</span></span>](./network/index.md) | <span data-ttu-id="6e9f4-119">Todos os elementos no esquema de configurações de rede.</span><span class="sxs-lookup"><span data-stu-id="6e9f4-119">All elements in the network settings schema.</span></span> |
| [<span data-ttu-id="6e9f4-120">**\<cryptographySettings>** Esquema de configurações</span><span class="sxs-lookup"><span data-stu-id="6e9f4-120">**\<cryptographySettings>** Settings Schema</span></span>](./cryptography/index.md) | <span data-ttu-id="6e9f4-121">Todos os elementos no esquema de configurações de criptografia.</span><span class="sxs-lookup"><span data-stu-id="6e9f4-121">All elements in the crypto settings schema.</span></span> |
| [<span data-ttu-id="6e9f4-122">**\<configuration>** Esquema de seções</span><span class="sxs-lookup"><span data-stu-id="6e9f4-122">**\<configuration>** Sections Schema</span></span>](configuration-sections-schema.md) | <span data-ttu-id="6e9f4-123">Todos os elementos na seção de configuração esquema de configurações.</span><span class="sxs-lookup"><span data-stu-id="6e9f4-123">All elements in the configuration section settings schema.</span></span> |
| [<span data-ttu-id="6e9f4-124">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="6e9f4-124">Trace and Debug Settings Schema</span></span>](./trace-debug/index.md) | <span data-ttu-id="6e9f4-125">Todos os elementos no esquema de configurações de rastreamento e depuração.</span><span class="sxs-lookup"><span data-stu-id="6e9f4-125">All elements in the trace and debug settings schema.</span></span> |
| <span data-ttu-id="6e9f4-126">[Esquema de definições de configuração do ASP.NET](/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="6e9f4-126">[ASP.NET Configuration Settings Schema](/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100))</span></span> | <span data-ttu-id="6e9f4-127">Todos os elementos no esquema de configuração do ASP.NET, que incluem elementos para configurar sites e aplicativos do ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="6e9f4-127">All elements in the ASP.NET configuration schema, which includes elements for configuring ASP.NET Web sites and applications.</span></span> <span data-ttu-id="6e9f4-128">Usado em arquivos *Web.config* .</span><span class="sxs-lookup"><span data-stu-id="6e9f4-128">Used in *Web.config* files.</span></span> |
| <span data-ttu-id="6e9f4-129">[**\<webServices>** Esquema de configurações](/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="6e9f4-129">[**\<webServices>** Settings Schema](/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100))</span></span> | <span data-ttu-id="6e9f4-130">Todos os elementos no esquema de configurações de serviços Web.</span><span class="sxs-lookup"><span data-stu-id="6e9f4-130">All elements in the Web services settings schema.</span></span> |
| [<span data-ttu-id="6e9f4-131">Esquema de configurações da Web</span><span class="sxs-lookup"><span data-stu-id="6e9f4-131">Web Settings Schema</span></span>](./web/index.md) | <span data-ttu-id="6e9f4-132">Todos os elementos do esquema de configurações da Web, que incluem elementos para configurar como o ASP.NET, funciona com um aplicativo host, como o IIS.</span><span class="sxs-lookup"><span data-stu-id="6e9f4-132">All elements in the Web settings schema, which includes elements for configuring how ASP.NET works with a host application such as IIS.</span></span> <span data-ttu-id="6e9f4-133">Usado em arquivos *aspnet.config* .</span><span class="sxs-lookup"><span data-stu-id="6e9f4-133">Used in *aspnet.config* files.</span></span> |

## <a name="remarks"></a><span data-ttu-id="6e9f4-134">Comentários</span><span class="sxs-lookup"><span data-stu-id="6e9f4-134">Remarks</span></span>

<span data-ttu-id="6e9f4-135">Cada arquivo de configuração deve conter exatamente um **\<configuration>** elemento.</span><span class="sxs-lookup"><span data-stu-id="6e9f4-135">Each configuration file must contain exactly one **\<configuration>** element.</span></span>

## <a name="see-also"></a><span data-ttu-id="6e9f4-136">Confira também</span><span class="sxs-lookup"><span data-stu-id="6e9f4-136">See also</span></span>

- [<span data-ttu-id="6e9f4-137">Esquema do arquivo de configuração para o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="6e9f4-137">Configuration file schema for the .NET Framework</span></span>](index.md)
