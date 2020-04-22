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
# <a name="install-extra-mlnet-dependencies"></a>Instale dependências extras de ML.NET

Na maioria dos casos, em todos os sistemas operacionais, instalar ML.NET é tão simples quanto referenciar o pacote NuGet apropriado.

```bash
dotnet add package Microsoft.ML
```

Em alguns casos, porém, existem requisitos adicionais de instalação, especialmente quando os componentes nativos são necessários. Este documento descreve os requisitos de instalação para esses casos. As seções são divididas `Microsoft.ML.*` pelo pacote NuGet específico que tem a dependência adicional.

## <a name="microsoftmltimeseries-microsoftmlautoml"></a>Microsoft.ML.TimeSeries, Microsoft.ML.AutoML

Ambos os pacotes têm uma `Microsoft.ML.MKL.Redist`dependência, que tem `libiomp`uma dependência de .

### <a name="windows"></a>Windows

Não são necessárias etapas extras de instalação. A biblioteca é instalada quando o pacote NuGet é adicionado ao projeto.

### <a name="linux"></a>Linux

1. Instale a chave GPG para o repositório

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

2. Adicione o repositório APT para MKL

    ```bash
    sudo sh -c 'echo deb https://apt.repos.intel.com/mkl all main > /etc/apt/sources.list.d/intel-mkl.list'
    ```

3. Atualizar pacotes

    ```bash
    sudo apt-get update
    ```

4. Instalar o MKL

    ```bash
    sudo apt-get install <COMPONENT>-<VERSION>.<UPDATE>-<BUILD_NUMBER>
    ```

    Por exemplo:

    ```bash
    sudo apt-get install intel-mkl-64bit-2020.0-088
    ```

    Determinar a localização de`libiomp.so`

    ```bash
    find /opt -name "libiomp5.so"
    ```

    Por exemplo:

    ```output
    /opt/intel/compilers_and_libraries_2020.0.166/linux/compiler/lib/intel64_lin/libiomp5.so
    ```

5. Adicione este local ao caminho da biblioteca de carga:

    ```bash
    sudo ldconfig /opt/intel/compilers_and_libraries_2020.0.166/linux/compiler/lib/intel64_lin
    ```

### <a name="mac"></a>Mac

1. Instale a biblioteca com`Homebrew`

    ```bash
    brew update && brew install https://raw.githubusercontent.com/Homebrew/homebrew-core/f5b1ac99a7fba27c19cee0bc4f036775c889b359/Formula/libomp.rb && brew link libomp --force
    ```
