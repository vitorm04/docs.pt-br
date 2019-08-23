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
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921247"
---
# <a name="configuration-element"></a><span data-ttu-id="f54ba-102">\<elemento de > de configuração</span><span class="sxs-lookup"><span data-stu-id="f54ba-102">\<configuration> element</span></span>

<span data-ttu-id="f54ba-103">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f54ba-103">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>

<span data-ttu-id="f54ba-104">**\<configuration>**</span><span class="sxs-lookup"><span data-stu-id="f54ba-104">**\<configuration>**</span></span>

## <a name="syntax"></a><span data-ttu-id="f54ba-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f54ba-105">Syntax</span></span>

```xml
<configuration>
  <!-- Configuration settings -->
</configuration>
```

## <a name="attributes"></a><span data-ttu-id="f54ba-106">Atributos</span><span class="sxs-lookup"><span data-stu-id="f54ba-106">Attributes</span></span>

<span data-ttu-id="f54ba-107">Nenhum</span><span class="sxs-lookup"><span data-stu-id="f54ba-107">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="f54ba-108">Elemento pai</span><span class="sxs-lookup"><span data-stu-id="f54ba-108">Parent element</span></span>

<span data-ttu-id="f54ba-109">Nenhum</span><span class="sxs-lookup"><span data-stu-id="f54ba-109">None</span></span>

## <a name="child-elements"></a><span data-ttu-id="f54ba-110">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f54ba-110">Child elements</span></span>

|     | <span data-ttu-id="f54ba-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="f54ba-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="f54ba-112"> **\<assemblyBinding>** </span><span class="sxs-lookup"><span data-stu-id="f54ba-112">**\<assemblyBinding>**</span></span>](assemblybinding-element-for-configuration.md) | <span data-ttu-id="f54ba-113">Especifica a diretiva de ligação de assembly no nível de configuração.</span><span class="sxs-lookup"><span data-stu-id="f54ba-113">Specifies assembly binding policy at the configuration level.</span></span>|
| [<span data-ttu-id="f54ba-114">esquema de configurações de > de inicialização  **\<** </span><span class="sxs-lookup"><span data-stu-id="f54ba-114">**\<startup>** Settings Schema</span></span>](./startup/index.md) | <span data-ttu-id="f54ba-115">Todos os elementos no esquema de configurações de inicialização.</span><span class="sxs-lookup"><span data-stu-id="f54ba-115">All elements in the startup settings schema.</span></span> |
| [<span data-ttu-id="f54ba-116">esquema de configurações de > de tempo de execução  **\<** </span><span class="sxs-lookup"><span data-stu-id="f54ba-116">**\<runtime>** Settings Schema</span></span>](./runtime/index.md) | <span data-ttu-id="f54ba-117">Todos os elementos no esquema de configurações de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="f54ba-117">All elements in the runtime settings schema.</span></span> |
| <span data-ttu-id="f54ba-118">[ **\<system.runtime.remoting>** Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="f54ba-118">[**\<system.runtime.remoting>** Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100))</span></span> | <span data-ttu-id="f54ba-119">Todos os elementos no esquema de configurações de comunicação remota.</span><span class="sxs-lookup"><span data-stu-id="f54ba-119">All elements in the remoting settings schema.</span></span> |
| [<span data-ttu-id="f54ba-120">esquema de configurações do **System .net > \<** </span><span class="sxs-lookup"><span data-stu-id="f54ba-120">**\<system.Net>** Settings Schema</span></span>](./network/index.md) | <span data-ttu-id="f54ba-121">Todos os elementos no esquema de configurações de rede.</span><span class="sxs-lookup"><span data-stu-id="f54ba-121">All elements in the network settings schema.</span></span> |
| [<span data-ttu-id="f54ba-122">esquema de configurações de > de cryptographySettings  **\<** </span><span class="sxs-lookup"><span data-stu-id="f54ba-122">**\<cryptographySettings>** Settings Schema</span></span>](./cryptography/index.md) | <span data-ttu-id="f54ba-123">Todos os elementos no esquema de configurações de criptografia.</span><span class="sxs-lookup"><span data-stu-id="f54ba-123">All elements in the crypto settings schema.</span></span> |
| [<span data-ttu-id="f54ba-124">esquema de seções de > de configuração  **\<** </span><span class="sxs-lookup"><span data-stu-id="f54ba-124">**\<configuration>** Sections Schema</span></span>](configuration-sections-schema.md) | <span data-ttu-id="f54ba-125">Todos os elementos na seção de configuração esquema de configurações.</span><span class="sxs-lookup"><span data-stu-id="f54ba-125">All elements in the configuration section settings schema.</span></span> |
| [<span data-ttu-id="f54ba-126">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="f54ba-126">Trace and Debug Settings Schema</span></span>](./trace-debug/index.md) | <span data-ttu-id="f54ba-127">Todos os elementos no esquema de configurações de rastreamento e depuração.</span><span class="sxs-lookup"><span data-stu-id="f54ba-127">All elements in the trace and debug settings schema.</span></span> |
| <span data-ttu-id="f54ba-128">[Esquema de definições de configuração do ASP.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="f54ba-128">[ASP.NET Configuration Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100))</span></span> | <span data-ttu-id="f54ba-129">Todos os elementos no esquema de configuração do ASP.NET, que incluem elementos para configurar sites e aplicativos do ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="f54ba-129">All elements in the ASP.NET configuration schema, which includes elements for configuring ASP.NET Web sites and applications.</span></span> <span data-ttu-id="f54ba-130">Usado em arquivos *Web. config* .</span><span class="sxs-lookup"><span data-stu-id="f54ba-130">Used in *Web.config* files.</span></span> |
| <span data-ttu-id="f54ba-131">[esquema de configurações de > de WebServices  **\<** ](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="f54ba-131">[**\<webServices>** Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100))</span></span> | <span data-ttu-id="f54ba-132">Todos os elementos no esquema de configurações de serviços Web.</span><span class="sxs-lookup"><span data-stu-id="f54ba-132">All elements in the Web services settings schema.</span></span> |
| [<span data-ttu-id="f54ba-133">Esquema de configurações Web</span><span class="sxs-lookup"><span data-stu-id="f54ba-133">Web Settings Schema</span></span>](./web/index.md) | <span data-ttu-id="f54ba-134">Todos os elementos do esquema de configurações da Web, que incluem elementos para configurar como o ASP.NET, funciona com um aplicativo host, como o IIS.</span><span class="sxs-lookup"><span data-stu-id="f54ba-134">All elements in the Web settings schema, which includes elements for configuring how ASP.NET works with a host application such as IIS.</span></span> <span data-ttu-id="f54ba-135">Usado em arquivos *ASPNET. config* .</span><span class="sxs-lookup"><span data-stu-id="f54ba-135">Used in *aspnet.config* files.</span></span> |

## <a name="remarks"></a><span data-ttu-id="f54ba-136">Comentários</span><span class="sxs-lookup"><span data-stu-id="f54ba-136">Remarks</span></span>

<span data-ttu-id="f54ba-137">Cada arquivo de configuração deve conter exatamente  **\<** um elemento de > de configuração.</span><span class="sxs-lookup"><span data-stu-id="f54ba-137">Each configuration file must contain exactly one **\<configuration>** element.</span></span>

## <a name="see-also"></a><span data-ttu-id="f54ba-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f54ba-138">See also</span></span>

- [<span data-ttu-id="f54ba-139">Esquema do arquivo de configuração para o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f54ba-139">Configuration file schema for the .NET Framework</span></span>](index.md)
