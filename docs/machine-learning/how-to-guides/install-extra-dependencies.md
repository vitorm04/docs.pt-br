---
title: Instale dependências extras de ML.NET
description: Saiba como instalar quaisquer bibliotecas nativas das quais ML.NET pacotes dependem, mas não sejam instalados com os pacotes NuGet
ms.date: 04/02/2020
author: natke
ms.author: nakersha
ms.custom: how-to
ms.openlocfilehash: c427439d0950bfea38f1d6d11af84216e0f1965f
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021850"
---
# <a name="install-extra-mlnet-dependencies"></a><span data-ttu-id="088aa-103">Instale dependências extras de ML.NET</span><span class="sxs-lookup"><span data-stu-id="088aa-103">Install extra ML.NET dependencies</span></span>

<span data-ttu-id="088aa-104">Na maioria dos casos, em todos os sistemas operacionais, instalar ML.NET é tão simples quanto referenciar o pacote NuGet apropriado.</span><span class="sxs-lookup"><span data-stu-id="088aa-104">In most cases, on all operating systems, installing ML.NET is as simple as referencing the appropriate NuGet package.</span></span>

```bash
dotnet add package Microsoft.ML
```

<span data-ttu-id="088aa-105">Em alguns casos, porém, existem requisitos adicionais de instalação, especialmente quando os componentes nativos são necessários.</span><span class="sxs-lookup"><span data-stu-id="088aa-105">In some cases though, there are additional installation requirements, particularly when native components are required.</span></span> <span data-ttu-id="088aa-106">Este documento descreve os requisitos de instalação para esses casos.</span><span class="sxs-lookup"><span data-stu-id="088aa-106">This document describes the installation requirements for those cases.</span></span> <span data-ttu-id="088aa-107">As seções são divididas `Microsoft.ML.*` pelo pacote NuGet específico que tem a dependência adicional.</span><span class="sxs-lookup"><span data-stu-id="088aa-107">The sections are broken down by the specific `Microsoft.ML.*` NuGet package that has the additional dependency.</span></span>

## <a name="microsoftmltimeseries-microsoftmlautoml"></a><span data-ttu-id="088aa-108">Microsoft.ML.TimeSeries, Microsoft.ML.AutoML</span><span class="sxs-lookup"><span data-stu-id="088aa-108">Microsoft.ML.TimeSeries, Microsoft.ML.AutoML</span></span>

<span data-ttu-id="088aa-109">Ambos os pacotes têm uma `Microsoft.ML.MKL.Redist`dependência, que tem `libiomp`uma dependência de .</span><span class="sxs-lookup"><span data-stu-id="088aa-109">Both of these packages have a dependency on `Microsoft.ML.MKL.Redist`, which has a dependency on `libiomp`.</span></span>

### <a name="windows"></a><span data-ttu-id="088aa-110">Windows</span><span class="sxs-lookup"><span data-stu-id="088aa-110">Windows</span></span>

<span data-ttu-id="088aa-111">Não são necessárias etapas extras de instalação.</span><span class="sxs-lookup"><span data-stu-id="088aa-111">No extra installation steps required.</span></span> <span data-ttu-id="088aa-112">A biblioteca é instalada quando o pacote NuGet é adicionado ao projeto.</span><span class="sxs-lookup"><span data-stu-id="088aa-112">The library is installed when the NuGet package is added to the project.</span></span>

### <a name="linux"></a><span data-ttu-id="088aa-113">Linux</span><span class="sxs-lookup"><span data-stu-id="088aa-113">Linux</span></span>

1. <span data-ttu-id="088aa-114">Instale a chave GPG para o repositório</span><span class="sxs-lookup"><span data-stu-id="088aa-114">Install the GPG key for the repository</span></span>

    ```bash
    sudo bash
    # <type your user password when prompted.  this will put you in a root shell>
    # cd to /tmp where this shell has write permission
    cd /tmp
    # now get the key:
    wget https://apt.repos.intel.com/intel-gpg-keys/GPG-PUB-KEY-INTEL-SW-PRODUCTS-2019.PUB
    # now install that key
    apt-key add GPG-PUB-KEY-INTEL-SW-PRODUCTS-2019.PUB
    # now remove the public key file exit the root shell
    rm GPG-PUB-KEY-INTEL-SW-PRODUCTS-2019.PUB
    exit
    ```

2. <span data-ttu-id="088aa-115">Adicione o repositório APT para MKL</span><span class="sxs-lookup"><span data-stu-id="088aa-115">Add the APT Repository for MKL</span></span>

    ```bash
    sudo sh -c 'echo deb https://apt.repos.intel.com/mkl all main > /etc/apt/sources.list.d/intel-mkl.list'
    ```

3. <span data-ttu-id="088aa-116">Atualizar pacotes</span><span class="sxs-lookup"><span data-stu-id="088aa-116">Update packages</span></span>

    ```bash
    sudo apt-get update
    ```

4. <span data-ttu-id="088aa-117">Instalar o MKL</span><span class="sxs-lookup"><span data-stu-id="088aa-117">Install MKL</span></span>

    ```bash
    sudo apt-get install <COMPONENT>-<VERSION>.<UPDATE>-<BUILD_NUMBER>
    ```

    <span data-ttu-id="088aa-118">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="088aa-118">For example:</span></span>

    ```bash
    sudo apt-get install intel-mkl-64bit-2020.0-088
    ```

    <span data-ttu-id="088aa-119">Determinar a localização de`libiomp.so`</span><span class="sxs-lookup"><span data-stu-id="088aa-119">Determine the location of `libiomp.so`</span></span>

    ```bash
    find /opt -name "libiomp5.so"
    ```

    <span data-ttu-id="088aa-120">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="088aa-120">For example:</span></span>

    ```output
    /opt/intel/compilers_and_libraries_2020.0.166/linux/compiler/lib/intel64_lin/libiomp5.so
    ```

5. <span data-ttu-id="088aa-121">Adicione este local ao caminho da biblioteca de carga:</span><span class="sxs-lookup"><span data-stu-id="088aa-121">Add this location to the load library path:</span></span>

    ```bash
    sudo ldconfig /opt/intel/compilers_and_libraries_2020.0.166/linux/compiler/lib/intel64_lin
    ```

### <a name="mac"></a><span data-ttu-id="088aa-122">Mac</span><span class="sxs-lookup"><span data-stu-id="088aa-122">Mac</span></span>

1. <span data-ttu-id="088aa-123">Instale a biblioteca com`Homebrew`</span><span class="sxs-lookup"><span data-stu-id="088aa-123">Install the library with `Homebrew`</span></span>

    ```bash
    brew update && brew install https://raw.githubusercontent.com/Homebrew/homebrew-core/f5b1ac99a7fba27c19cee0bc4f036775c889b359/Formula/libomp.rb && brew link libomp --force
    ```
