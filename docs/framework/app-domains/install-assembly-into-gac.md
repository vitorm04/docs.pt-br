---
title: Como instalar um assembly no cache de assembly global
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- Gacutil.exe
- strong-named assemblies, global assembly cache
- global assembly cache, installing assemblies
- Global Assembly Cache tool
- windows installer, global assembly cache
ms.assetid: a7e6f091-d02c-49ba-b736-7295cb0eb743
ms.openlocfilehash: 64878a795a7c5b790c8991064e32b82505685c0c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155557"
---
# <a name="how-to-install-an-assembly-into-the-global-assembly-cache"></a>Como instalar um assembly no cache de assembly global

O cache de assembly global armazena os assemblies que vários aplicativos compartilham. Instale um assembly no [cache de assembly global](gac.md) com um dos seguintes componentes:

- [Windows Installer](#windows-installer)
- [Ferramenta cache de assembly global](#global-assembly-cache-tool)

> [!IMPORTANT]
> Você pode instalar somente assemblies de nome forte no cache de assembly global. Para obter informações sobre como criar um assembly de nome forte, consulte [como assinar um assembly com um nome forte](../../standard/assembly/sign-strong-name.md).

## <a name="windows-installer"></a>Windows Installer

[Windows Installer](/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache), o mecanismo de instalação do Windows, é a maneira recomendada de adicionar assemblies ao cache de assembly global. O Windows Installer fornece uma contagem de referências de assemblies no cache de assembly global e outros benefícios. Para criar um pacote do instalador do Windows Installer, use a [extensão de conjunto de ferramentas WiX do Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension).

## <a name="global-assembly-cache-tool"></a>Ferramenta Cache de Assembly Global

Você pode usar o [Utilitário de cache de assembly global do .net (Gacutil. exe)](../tools/gacutil-exe-gac-tool.md) para adicionar assemblies ao cache de assembly global e para exibir o conteúdo do cache de assembly global.

   > [!NOTE]
   > O *gacutil.exe* é indicado apenas para fins de desenvolvimento. Não o use para instalar assemblies de produção no cache de assembly global.

A sintaxe para usar o *gacutil.exe* para instalar um assembly no cache de assembly global é a seguinte:

```cmd
gacutil -i <assembly name>
```

Neste comando, * \<o nome do assembly>* é o nome do assembly a ser instalado no cache de assembly global.

Se o *Gacutil. exe* não estiver no caminho do sistema, use o [prompt de comando do desenvolvedor para a versão vs * \<>* ](../tools/developer-command-prompt-for-vs.md).

O exemplo a seguir instala um assembly com o nome do arquivo *hello.dll* no cache de assembly global.

```cmd
gacutil -i hello.dll
```

> [!NOTE]
> Nas versões anteriores do .NET Framework, a extensão do shell do Windows *Shfusion.dll* permitia a instalação de assemblies arrastando-os no Explorador de Arquivos. Começando no .NET Framework 4, a *Shfusion.dll* ficou obsoleta.

## <a name="see-also"></a>Confira também

- [Trabalhar com assemblies e o cache de assembly global](working-with-assemblies-and-the-gac.md)
- [Como: remover um assembly do cache de assembly global](how-to-remove-an-assembly-from-the-gac.md)
- [Gacutil. exe (ferramenta global assembly cache)](../tools/gacutil-exe-gac-tool.md)
- [Como assinar um assembly com um nome forte](../../standard/assembly/sign-strong-name.md)
