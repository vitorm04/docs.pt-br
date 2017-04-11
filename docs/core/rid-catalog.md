---
title: "Catálogo do RID (Identificador de Tempo de Execução) do .NET Core"
description: "Catálogo do RID (Identificador de Tempo de Execução) do .NET Core"
keywords: .NET, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 08/22/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: b2032f5d-771f-48d9-917c-587d9509035c
translationtype: Human Translation
ms.sourcegitcommit: 811b9539019b7cc2817b5742760ae52fbc2f95dd
ms.openlocfilehash: fc59a9f3333f01caf9622dd500a5de6e2ae5132b
ms.lasthandoff: 03/02/2017

---

# <a name="net-core-runtime-identifier-rid-catalog"></a>Catálogo do RID (Identificador de Tempo de Execução) do .NET Core

## <a name="what-are-rids"></a>O que são RIDs?
RID é a abreviação de *Identificador de Tempo de Execução*. RIDs são usados para identificar os sistemas operacionais de destino em que um aplicativo ou ativo (ou seja, o assembly) será executado. Eles assemelham-se a: "ubuntu.14.04-x64", "win7-x64" e "osx.10.11-x64". Para os pacotes com dependências nativas, ele designará as plataformas em que o pacote pode ser restaurado. 

É importante observar que os RIDs são cadeias de caracteres realmente opacas. Isso significa que eles devem corresponder exatamente para as operações que os utilizam poderem funcionar. Por exemplo, vamos considerar o caso do [Elementary OS](https://elementary.io/), que é um clone simples do Ubuntu 14.04. Embora .NET Core e CLI funcionem nessa versão do Ubuntu, se você tentar usá-los no Elementary OS sem modificações, a operação de restauração de qualquer pacote falhará. Isso ocorre porque atualmente não temos um RID que designa o Elementary OS como uma plataforma. 

RIDs que representem sistemas operacionais concretos geralmente seguem este padrão: `[os].[version]-[arch]` em que:
- `[os]` é o moniker do sistema operacional, por exemplo, `ubuntu`.
- `[version]` é a versão do sistema operacional na forma de um número de versão separado por ponto (`.`), por exemplo, `15.10`, preciso o suficiente para permitir que ativos sejam direcionados para as APIs da plataforma do sistema operacional representado por essa versão.
  - Elas **não** devem ser versões comerciais, pois essas geralmente representam várias versões distintas do sistema operacional com diferentes áreas de superfície de API da plataforma.
- `[arch]` é a arquitetura do processador, por exemplo, `x86`, `x64`, `arm`, `arm64` etc.

O gráfico RID é definido em um pacote chamado `Microsoft.NETCore.Platforms` em um arquivo chamado `runtime.json`, que você pode encontrar no [repositório CoreFX](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json). Se você usar esse arquivo, notará que alguns RIDs têm uma instrução `"#import"`. Essas são instruções de compatibilidade. Isso significa que um RID que contém um RID importado pode ser direcionado para restaurar pacotes para esse RID. Parece um pouco confuso, mas vejamos um exemplo. Vamos dar uma olhada no macOS:

```json
"osx.10.11-x64": {
    "#import": [ "osx.10.11", "osx.10.10-x64" ]
}
```
O RID acima especifica que `osx.10.11-x64` importa `osx.10.10-x64`. Isso significa que, ao restaurar pacotes, o NuGet poderá restaurar pacotes que especificam que precisam de `osx.10.10-x64` em `osx.10.11-x64`.

Um exemplo de gráfico RID ligeiramente maior:  

- `win10-arm`
  - `win10`
  - `win81-arm`
    - `win81`
    - `win8-arm`
      - `win8`
        - `win7`
          - `win`
            - `any`

Todos os RIDs eventualmente mapeiam para a raiz de `any` RID.

Embora pareça fácil de usar, existem algumas coisas especiais sobre RIDs que você precisa ter em mente ao trabalhar com eles:

* Eles são **cadeias de caracteres opacas** e devem ser tratados como caixas pretas
    * Você não deve criar RIDs programaticamente
* Você precisa usar os RIDs que já estão definidos para a plataforma e este documento mostra isso
* Os RIDs precisam ser específicos, por isso não crie suposições com base no valor do real do RID. Consulte este documento para determinar qual RID(s) são necessário para uma determinada plataforma

## <a name="using-rids"></a>Usando RIDs
Para usar RIDs, você precisa saber quais RIDs existem. Novos RIDs são adicionados regularmente para a plataforma. Para a versão mais recente, consulte o arquivo [runtime.json](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) no repositório CoreFX.

> [!NOTE]
> Estamos trabalhando para disponibilizar essas informações em um formato mais interativo. Quando isso acontecer, esta página será atualizada para indicar a essa ferramenta e/ou sua documentação de uso. 

## <a name="windows-rids"></a>RIDs do Windows

* Windows 7 / Windows Server 2008 R2
    * `win7-x64`
    * `win7-x86`
* Windows 8 / Windows Server 2012
    * `win8-x64`
    * `win8-x86`
    * `win8-arm`
* Windows 8.1 / Windows Server 2012 R2
    * `win81-x64`
    * `win81-x86`
    * `win81-arm`
* Windows 10 / Windows Server 2016
    * `win10-x64`
    * `win10-x86`
    * `win10-arm`
    * `win10-arm64`

## <a name="linux-rids"></a>RIDs do Linux

* Red Hat Enterprise Linux
    * `rhel.7-x64`
* Ubuntu
    * `ubuntu.14.04-x64`
    * `ubuntu.14.10-x64`
    * `ubuntu.15.04-x64`
    * `ubuntu.15.10-x64`
    * `ubuntu.16.04-x64`
    * `ubuntu.16.10-x64`
* CentOS
    * `centos.7-x64`
* Debian
    * `debian.8-x64`
* Fedora
    * `fedora.23-x64`
    * `fedora.24-x64`
* OpenSUSE
    * `opensuse.13.2-x64`
    * `opensuse.42.1-x64`
* Oracle Linux
    * `ol.7-x64`
    * `ol.7.0-x64`
    * `ol.7.1-x64`
    * `ol.7.2-x64`
* Derivados do Ubuntu com suporte no momento 
    * `linuxmint.17-x64`
    * `linuxmint.17.1-x64`
    * `linuxmint.17.2-x64`
    * `linuxmint.17.3-x64`
    * `linuxmint.18-x64`

## <a name="os-x-rids"></a>RIDs do OS X

* `osx.10.10-x64`
* `osx.10.11-x64`
* `osx.10.12-x64`

