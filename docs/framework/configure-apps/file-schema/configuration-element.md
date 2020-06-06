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
ms.openlocfilehash: 0e09ec49024b769c516fd97085904781f64b4486
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "69921247"
---
# <a name="configuration-element"></a><span data-ttu-id="8df7d-102">Elemento \<configuration></span><span class="sxs-lookup"><span data-stu-id="8df7d-102">\<configuration> element</span></span>

<span data-ttu-id="8df7d-103">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8df7d-103">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>

**\<configuration>**

## <a name="syntax"></a><span data-ttu-id="8df7d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8df7d-104">Syntax</span></span>

```xml
<configuration>
  <!-- Configuration settings -->
</configuration>
```

## <a name="attributes"></a><span data-ttu-id="8df7d-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="8df7d-105">Attributes</span></span>

<span data-ttu-id="8df7d-106">Nenhum</span><span class="sxs-lookup"><span data-stu-id="8df7d-106">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="8df7d-107">Elemento pai</span><span class="sxs-lookup"><span data-stu-id="8df7d-107">Parent element</span></span>

<span data-ttu-id="8df7d-108">Nenhum</span><span class="sxs-lookup"><span data-stu-id="8df7d-108">None</span></span>

## <a name="child-elements"></a><span data-ttu-id="8df7d-109">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="8df7d-109">Child elements</span></span>

|     | <span data-ttu-id="8df7d-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="8df7d-110">Description</span></span> |
| --- | ----------- |
| [**\<assemblyBinding>**](assemblybinding-element-for-configuration.md) | <span data-ttu-id="8df7d-111">Especifica a diretiva de ligação de assembly no nível de configuração.</span><span class="sxs-lookup"><span data-stu-id="8df7d-111">Specifies assembly binding policy at the configuration level.</span></span>|
| [<span data-ttu-id="8df7d-112">**\<startup>** Esquema de configurações</span><span class="sxs-lookup"><span data-stu-id="8df7d-112">**\<startup>** Settings Schema</span></span>](./startup/index.md) | <span data-ttu-id="8df7d-113">Todos os elementos no esquema de configurações de inicialização.</span><span class="sxs-lookup"><span data-stu-id="8df7d-113">All elements in the startup settings schema.</span></span> |
| [<span data-ttu-id="8df7d-114">**\<runtime>** Esquema de configurações</span><span class="sxs-lookup"><span data-stu-id="8df7d-114">**\<runtime>** Settings Schema</span></span>](./runtime/index.md) | <span data-ttu-id="8df7d-115">Todos os elementos no esquema de configurações de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="8df7d-115">All elements in the runtime settings schema.</span></span> |
| <span data-ttu-id="8df7d-116">[**\<system.runtime.remoting>** Esquema de configurações](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="8df7d-116">[**\<system.runtime.remoting>** Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100))</span></span> | <span data-ttu-id="8df7d-117">Todos os elementos no esquema de configurações de comunicação remota.</span><span class="sxs-lookup"><span data-stu-id="8df7d-117">All elements in the remoting settings schema.</span></span> |
| [<span data-ttu-id="8df7d-118">**\<system.Net>** Esquema de configurações</span><span class="sxs-lookup"><span data-stu-id="8df7d-118">**\<system.Net>** Settings Schema</span></span>](./network/index.md) | <span data-ttu-id="8df7d-119">Todos os elementos no esquema de configurações de rede.</span><span class="sxs-lookup"><span data-stu-id="8df7d-119">All elements in the network settings schema.</span></span> |
| [<span data-ttu-id="8df7d-120">**\<cryptographySettings>** Esquema de configurações</span><span class="sxs-lookup"><span data-stu-id="8df7d-120">**\<cryptographySettings>** Settings Schema</span></span>](./cryptography/index.md) | <span data-ttu-id="8df7d-121">Todos os elementos no esquema de configurações de criptografia.</span><span class="sxs-lookup"><span data-stu-id="8df7d-121">All elements in the crypto settings schema.</span></span> |
| [<span data-ttu-id="8df7d-122">**\<configuration>** Esquema de seções</span><span class="sxs-lookup"><span data-stu-id="8df7d-122">**\<configuration>** Sections Schema</span></span>](configuration-sections-schema.md) | <span data-ttu-id="8df7d-123">Todos os elementos na seção de configuração esquema de configurações.</span><span class="sxs-lookup"><span data-stu-id="8df7d-123">All elements in the configuration section settings schema.</span></span> |
| [<span data-ttu-id="8df7d-124">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="8df7d-124">Trace and Debug Settings Schema</span></span>](./trace-debug/index.md) | <span data-ttu-id="8df7d-125">Todos os elementos no esquema de configurações de rastreamento e depuração.</span><span class="sxs-lookup"><span data-stu-id="8df7d-125">All elements in the trace and debug settings schema.</span></span> |
| <span data-ttu-id="8df7d-126">[Esquema de definições de configuração do ASP.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="8df7d-126">[ASP.NET Configuration Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100))</span></span> | <span data-ttu-id="8df7d-127">Todos os elementos no esquema de configuração do ASP.NET, que incluem elementos para configurar sites e aplicativos do ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="8df7d-127">All elements in the ASP.NET configuration schema, which includes elements for configuring ASP.NET Web sites and applications.</span></span> <span data-ttu-id="8df7d-128">Usado em arquivos *Web. config* .</span><span class="sxs-lookup"><span data-stu-id="8df7d-128">Used in *Web.config* files.</span></span> |
| <span data-ttu-id="8df7d-129">[**\<webServices>** Esquema de configurações](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="8df7d-129">[**\<webServices>** Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100))</span></span> | <span data-ttu-id="8df7d-130">Todos os elementos no esquema de configurações de serviços Web.</span><span class="sxs-lookup"><span data-stu-id="8df7d-130">All elements in the Web services settings schema.</span></span> |
| [<span data-ttu-id="8df7d-131">Esquema de configurações Web</span><span class="sxs-lookup"><span data-stu-id="8df7d-131">Web Settings Schema</span></span>](./web/index.md) | <span data-ttu-id="8df7d-132">Todos os elementos do esquema de configurações da Web, que incluem elementos para configurar como o ASP.NET, funciona com um aplicativo host, como o IIS.</span><span class="sxs-lookup"><span data-stu-id="8df7d-132">All elements in the Web settings schema, which includes elements for configuring how ASP.NET works with a host application such as IIS.</span></span> <span data-ttu-id="8df7d-133">Usado em arquivos *ASPNET. config* .</span><span class="sxs-lookup"><span data-stu-id="8df7d-133">Used in *aspnet.config* files.</span></span> |

## <a name="remarks"></a><span data-ttu-id="8df7d-134">Comentários</span><span class="sxs-lookup"><span data-stu-id="8df7d-134">Remarks</span></span>

<span data-ttu-id="8df7d-135">Cada arquivo de configuração deve conter exatamente um **\<configuration>** elemento.</span><span class="sxs-lookup"><span data-stu-id="8df7d-135">Each configuration file must contain exactly one **\<configuration>** element.</span></span>

## <a name="see-also"></a><span data-ttu-id="8df7d-136">Confira também</span><span class="sxs-lookup"><span data-stu-id="8df7d-136">See also</span></span>

- [<span data-ttu-id="8df7d-137">Esquema do arquivo de configuração para o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="8df7d-137">Configuration file schema for the .NET Framework</span></span>](index.md)
