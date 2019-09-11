---
title: Expor componentes do .NET Core ao COM
ms.date: 07/12/2019
helpviewer_keywords:
- exposing .NET Core components to COM
- interoperation with unmanaged code, exposing .NET Core components
- COM interop, exposing COM components
ms.assetid: 21271167-fe7f-46ba-a81f-a6812ea649d4
author: jkoritzinsky
ms.author: jekoritz
ms.openlocfilehash: 686d1b31478121a8b2c907d99672a5fcc3438a71
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70849032"
---
# <a name="exposing-net-core-components-to-com"></a><span data-ttu-id="23ee9-102">Expor componentes do .NET Core ao COM</span><span class="sxs-lookup"><span data-stu-id="23ee9-102">Exposing .NET Core Components to COM</span></span>

<span data-ttu-id="23ee9-103">No .NET Core, o processo de expor seus objetos .NET ao COM foi significativamente simplificado em comparação com o .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="23ee9-103">In .NET Core, the process for exposing your .NET objects to COM has been significantly streamlined in comparison to .NET Framework.</span></span> <span data-ttu-id="23ee9-104">O processo a seguir explicará como expor uma classe ao COM.</span><span class="sxs-lookup"><span data-stu-id="23ee9-104">The following process will walk you through how to expose a class to COM.</span></span> <span data-ttu-id="23ee9-105">Este tutorial mostra como:</span><span class="sxs-lookup"><span data-stu-id="23ee9-105">This tutorial shows you how to:</span></span>

- <span data-ttu-id="23ee9-106">Expor uma classe ao COM do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="23ee9-106">Expose a class to COM from .NET Core.</span></span>
- <span data-ttu-id="23ee9-107">Gerar um servidor COM como parte de criar sua biblioteca do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="23ee9-107">Generate a COM server as part of building your .NET Core library.</span></span>
- <span data-ttu-id="23ee9-108">Gerar automaticamente um manifesto de servidor lado a lado para COM Sem Registro.</span><span class="sxs-lookup"><span data-stu-id="23ee9-108">Automatically generate a side-by-side server manifest for Registry-Free COM.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="23ee9-109">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="23ee9-109">Prerequisites</span></span>

- <span data-ttu-id="23ee9-110">Instale o [SDK do .NET Core 3.0 Versão Prévia 7](https://dotnet.microsoft.com/download) ou uma versão mais recente.</span><span class="sxs-lookup"><span data-stu-id="23ee9-110">Install the [.NET Core 3.0 Preview 7 SDK](https://dotnet.microsoft.com/download) or a newer version.</span></span>

## <a name="create-the-library"></a><span data-ttu-id="23ee9-111">Criar a biblioteca</span><span class="sxs-lookup"><span data-stu-id="23ee9-111">Create the library</span></span>

<span data-ttu-id="23ee9-112">A primeira etapa é criar a biblioteca.</span><span class="sxs-lookup"><span data-stu-id="23ee9-112">The first step is to create the library.</span></span>

1. <span data-ttu-id="23ee9-113">Crie uma pasta e execute `dotnet new classlib` nela.</span><span class="sxs-lookup"><span data-stu-id="23ee9-113">Create a new folder, and in that folder run `dotnet new classlib`.</span></span>
2. <span data-ttu-id="23ee9-114">Abra `Class1.cs`.</span><span class="sxs-lookup"><span data-stu-id="23ee9-114">Open `Class1.cs`.</span></span>
3. <span data-ttu-id="23ee9-115">Adicione `using System.Runtime.InteropServices;` ao topo do arquivo.</span><span class="sxs-lookup"><span data-stu-id="23ee9-115">Add `using System.Runtime.InteropServices;` to the top of the file.</span></span>
4. <span data-ttu-id="23ee9-116">Crie uma interface chamada `IServer`.</span><span class="sxs-lookup"><span data-stu-id="23ee9-116">Create an interface named `IServer`.</span></span> <span data-ttu-id="23ee9-117">Por exemplo: [!code-csharp[The IServer interface](~/samples/core/extensions/COMServerDemo/COMContract/IServer.cs)]</span><span class="sxs-lookup"><span data-stu-id="23ee9-117">For example: [!code-csharp[The IServer interface](~/samples/core/extensions/COMServerDemo/COMContract/IServer.cs)]</span></span>
5. <span data-ttu-id="23ee9-118">Adicione o atributo `[Guid("<IID>")]` à interface, com o GUID da interface COM que você está implementando.</span><span class="sxs-lookup"><span data-stu-id="23ee9-118">Add the `[Guid("<IID>")]` attribute to the interface, with the interface GUID for the COM interface you're implementing.</span></span> <span data-ttu-id="23ee9-119">Por exemplo, `[Guid("fe103d6e-e71b-414c-80bf-982f18f6c1c7")]`.</span><span class="sxs-lookup"><span data-stu-id="23ee9-119">For example, `[Guid("fe103d6e-e71b-414c-80bf-982f18f6c1c7")]`.</span></span> <span data-ttu-id="23ee9-120">Observe que esse GUID precisa ser exclusivo, pois é o único identificador dessa interface para COM.</span><span class="sxs-lookup"><span data-stu-id="23ee9-120">Note that this GUID needs to be unique since it is the only identifier of this interface for COM.</span></span> <span data-ttu-id="23ee9-121">No Visual Studio, você pode gerar um GUID acessando Ferramentas > Criar GUID para abrir a ferramenta Criar GUID.</span><span class="sxs-lookup"><span data-stu-id="23ee9-121">In Visual Studio, you can generate a GUID by going to Tools > Create GUID to open the Create GUID tool.</span></span>
6. <span data-ttu-id="23ee9-122">Adicione o atributo `[InterfaceType]` à interface e especifique quais interfaces COM base sua interface deve implementar.</span><span class="sxs-lookup"><span data-stu-id="23ee9-122">Add the `[InterfaceType]` attribute to the interface and specify what base COM interfaces your interface should implement.</span></span>
7. <span data-ttu-id="23ee9-123">Crie uma classe chamada `Server` que implementa `IServer`.</span><span class="sxs-lookup"><span data-stu-id="23ee9-123">Create a class named `Server` that implements `IServer`.</span></span>
8. <span data-ttu-id="23ee9-124">Adicione o atributo `[Guid("<CLSID>")]` à classe, com o GUID do identificador de classe da classe COM que você está implementando.</span><span class="sxs-lookup"><span data-stu-id="23ee9-124">Add the `[Guid("<CLSID>")]` attribute to the class, with the class identifier GUID for the COM class you're implementing.</span></span> <span data-ttu-id="23ee9-125">Por exemplo, `[Guid("9f35b6f5-2c05-4e7f-93aa-ee087f6e7ab6")]`.</span><span class="sxs-lookup"><span data-stu-id="23ee9-125">For example, `[Guid("9f35b6f5-2c05-4e7f-93aa-ee087f6e7ab6")]`.</span></span> <span data-ttu-id="23ee9-126">Como ocorre com o GUID da interface, esse GUID deve ser exclusivo pois é o único identificador dessa interface para COM.</span><span class="sxs-lookup"><span data-stu-id="23ee9-126">As with the interface GUID, this GUID must be unique since it is the only identifier of this interface to COM.</span></span>
9. <span data-ttu-id="23ee9-127">Adicione o atributo `[ComVisible(true)]` à interface e à classe.</span><span class="sxs-lookup"><span data-stu-id="23ee9-127">Add the `[ComVisible(true)]` attribute to both the interface and the class.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="23ee9-128">Diferentemente do .NET Framework, o .NET Core exige que você especifique o CLSID de qualquer classe que você deseja que seja ativável por meio do COM.</span><span class="sxs-lookup"><span data-stu-id="23ee9-128">Unlike in .NET Framework, .NET Core requires you to specify the CLSID of any class you want to be activatable via COM.</span></span>

## <a name="generate-the-com-host"></a><span data-ttu-id="23ee9-129">Gerar o host COM</span><span class="sxs-lookup"><span data-stu-id="23ee9-129">Generate the COM host</span></span>

1. <span data-ttu-id="23ee9-130">Abra o arquivo de projeto `.csproj` e adicione `<EnableComHosting>true</EnableComHosting>` dentro de uma marca `<PropertyGroup></PropertyGroup>`.</span><span class="sxs-lookup"><span data-stu-id="23ee9-130">Open the `.csproj` project file and add `<EnableComHosting>true</EnableComHosting>` inside a `<PropertyGroup></PropertyGroup>` tag.</span></span>
2. <span data-ttu-id="23ee9-131">Compile o projeto.</span><span class="sxs-lookup"><span data-stu-id="23ee9-131">Build the project.</span></span>

<span data-ttu-id="23ee9-132">A saída resultante terá um arquivo `ProjectName.dll`, `ProjectName.deps.json`, `ProjectName.runtimeconfig.json` e `ProjectName.comhost.dll`.</span><span class="sxs-lookup"><span data-stu-id="23ee9-132">The resulting output will have a `ProjectName.dll`, `ProjectName.deps.json`, `ProjectName.runtimeconfig.json` and `ProjectName.comhost.dll` file.</span></span>

## <a name="register-the-com-host-for-com"></a><span data-ttu-id="23ee9-133">Registrar o host COM para COM</span><span class="sxs-lookup"><span data-stu-id="23ee9-133">Register the COM host for COM</span></span>

<span data-ttu-id="23ee9-134">Abra um prompt de comandos com privilégios elevados e execute `regsvr32 ProjectName.comhost.dll`.</span><span class="sxs-lookup"><span data-stu-id="23ee9-134">Open an elevated command prompt and run `regsvr32 ProjectName.comhost.dll`.</span></span> <span data-ttu-id="23ee9-135">Isso registrará todos os seus objetos .NET expostos com o COM.</span><span class="sxs-lookup"><span data-stu-id="23ee9-135">That will register all of your exposed .NET objects with COM.</span></span>

## <a name="enabling-regfree-com"></a><span data-ttu-id="23ee9-136">Habilitar o COM RegFree</span><span class="sxs-lookup"><span data-stu-id="23ee9-136">Enabling RegFree COM</span></span>

1. <span data-ttu-id="23ee9-137">Abra o arquivo de projeto `.csproj` e adicione `<EnableRegFreeCom>true</EnableRegFreeCom>` dentro de uma marca `<PropertyGroup></PropertyGroup>`.</span><span class="sxs-lookup"><span data-stu-id="23ee9-137">Open the `.csproj` project file and add `<EnableRegFreeCom>true</EnableRegFreeCom>` inside a `<PropertyGroup></PropertyGroup>` tag.</span></span>
2. <span data-ttu-id="23ee9-138">Compile o projeto.</span><span class="sxs-lookup"><span data-stu-id="23ee9-138">Build the project.</span></span>

<span data-ttu-id="23ee9-139">A saída resultante agora também terá um arquivo `ProjectName.X.manifest`.</span><span class="sxs-lookup"><span data-stu-id="23ee9-139">The resulting output will now also have a `ProjectName.X.manifest` file.</span></span> <span data-ttu-id="23ee9-140">Esse arquivo é o manifesto lado a lado para uso com o COM Sem Registro.</span><span class="sxs-lookup"><span data-stu-id="23ee9-140">This file is the side-by-side manifest for use with Registry-Free COM.</span></span>

## <a name="sample"></a><span data-ttu-id="23ee9-141">Amostra</span><span class="sxs-lookup"><span data-stu-id="23ee9-141">Sample</span></span>

<span data-ttu-id="23ee9-142">Há um [exemplo de servidor COM](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo) totalmente funcional no repositório dotnet/de exemplos no GitHub.</span><span class="sxs-lookup"><span data-stu-id="23ee9-142">There is a fully functional [COM server sample](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo) in the dotnet/samples repository on GitHub.</span></span>

## <a name="additional-notes"></a><span data-ttu-id="23ee9-143">Observações adicionais</span><span class="sxs-lookup"><span data-stu-id="23ee9-143">Additional Notes</span></span>

<span data-ttu-id="23ee9-144">Ao contrário do .NET Framework, não há suporte no .NET Core para gerar um TLB (Biblioteca de Tipos) COM com base em um assembly .NET Core.</span><span class="sxs-lookup"><span data-stu-id="23ee9-144">Unlike in .NET Framework, there is no support in .NET Core for generating a COM Type Library (TLB) from a .NET Core assembly.</span></span> <span data-ttu-id="23ee9-145">Você terá que escrever manualmente um arquivo IDL ou um cabeçalho C++ para as declarações nativas de suas interfaces.</span><span class="sxs-lookup"><span data-stu-id="23ee9-145">You will either have to manually write an IDL file or a C++ header for the native declarations of your interfaces.</span></span>

<span data-ttu-id="23ee9-146">Além disso, não há suporte para o carregamento do .NET Framework e do .NET Core no mesmo processo; em decorrência disso, não há suporte para o carregamento um servidor COM do .NET Core para um processo de cliente COM do .NET Framework ou vice-versa.</span><span class="sxs-lookup"><span data-stu-id="23ee9-146">Additionally, loading both .NET Framework and .NET Core into the same process is unsupported, and as a result loading a .NET Core COM server into a .NET Framework COM client process or vice versa is not supported.</span></span>
