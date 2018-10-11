---
title: Instalar um assembly no GAC
ms.date: 09/20/2018
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- Gacutil.exe
- strong-named assemblies, global assembly cache
- global assembly cache, installing assemblies
- Global Assembly Cache tool
- windows installer, global assembly cache
ms.assetid: a7e6f091-d02c-49ba-b736-7295cb0eb743
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d365ac77fe6cd7fc4fca36705729ec12b06d6830
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2018
ms.locfileid: "46584575"
---
# <a name="how-to-install-an-assembly-into-the-global-assembly-cache"></a>Como instalar um assembly no cache de assembly global

Há duas maneiras de instalar um assembly com nome forte no GAC (Cache de Assembly Global).

> [!IMPORTANT]
> Apenas os assemblies com nome forte podem ser instalados no GAC. Para obter informações sobre como criar um assembly de nome forte, consulte [Como assinar um assembly com um nome forte](how-to-sign-an-assembly-with-a-strong-name.md).

## <a name="windows-installer"></a>Windows Installer

[Windows Installer](/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache), o mecanismo de instalação do Windows, é a maneira recomendada de adicionar assemblies ao cache de assembly global. O Windows Installer fornece uma contagem de referências de assemblies no cache de assembly global e outros benefícios. É possível usar a extensão do [WiX Toolset para Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension) para criar um pacote de instalador para o Windows Installer.

## <a name="global-assembly-cache-tool"></a>Ferramenta de Cache de Assembly Global

É possível usar a [Ferramenta de Cache de Assembly Global (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) para adicionar assemblies com nome forte ao cache de assembly global e para exibir o conteúdo desse cache.

   > [!NOTE]
   > Gacutil.exe destina-se a fins de desenvolvimento e não deve ser usado para instalar assemblies de produção no Cache de Assembly Global.

A sintaxe de gacutil é a seguinte:

```shell
gacutil -i <assembly name>
```

Neste comando, *nome do assembly* é o nome do assembly a ser instalado no cache de assembly global.

O exemplo a seguir instala um assembly com nome de arquivo `hello.dll` no Cache de Assembly Global.

```shell
gacutil -i hello.dll
```

> [!NOTE]
> Nas versões anteriores do .NET Framework, a extensão do shell do Windows Shfusion.dll permitia instalar assemblies arrastando-os no **Explorador de Arquivos**. Do .NET Framework 4 em diante, a Shfusion.dll tornou-se obsoleta.

## <a name="see-also"></a>Consulte também

- [Como trabalhar com assemblies e o cache de assembly global](working-with-assemblies-and-the-gac.md)
- [Como remover um assembly do cache de assembly global](how-to-remove-an-assembly-from-the-gac.md)
- [Gacutil.exe (Ferramenta do Cache de Assemblies Global)](../tools/gacutil-exe-gac-tool.md)
- [Como assinar um assembly com um nome forte](how-to-sign-an-assembly-with-a-strong-name.md)