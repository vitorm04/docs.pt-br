---
title: "Portabilidade para .NET Core – Analisar suas dependências de terceiros"
description: "Portabilidade para .NET Core – Analisar suas dependências de terceiros"
keywords: .NET, .NET Core
author: cartermp
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: b446e9e0-72f6-48f6-92c6-70ad0ce3f86a
ms.workload: dotnetcore
ms.openlocfilehash: 70b39c9762e4ee7450d0f59455bace0ac728844c
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="porting-to-net-core---analyzing-your-third-party-party-dependencies"></a>Portabilidade para .NET Core – Analisar suas dependências de terceiros

A primeira etapa no processo de portabilidade é entender suas dependências de terceiros.  Você precisa descobrir quais delas, se houver, ainda não são executadas no .NET Core e desenvolver um plano de contingência para elas.

## <a name="prerequisites"></a>Pré-requisitos

Este artigo supõe que você está usando o Windows e o Visual Studio, e que você tem um código que é executado no .NET Framework atualmente.

## <a name="analyzing-nuget-packages"></a>Analisando Pacotes NuGet

É muito fácil analisar pacotes NuGet para portabilidade.  Como um pacote NuGet é essencialmente um conjunto de pastas que contêm assemblies específicos de plataforma, basta você verificar se há uma pasta que contém um assembly .NET Core.

Inspecionar as pastas do pacote NuGet é mais fácil com a ferramenta [Explorador de Pacotes NuGet](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer).  Veja como fazer isso.

1. Baixe e abra o Explorador de Pacotes NuGet.
2. Clique em "Abrir pacote de feed online".
3. Pesquise o nome do pacote.
4. Expanda a pasta "lib" no lado direito e observe os nomes de pasta.

Você também pode ver o que tem suporte em um pacote em [nuget.org](https://www.nuget.org/) na seção **Dependências** da página desse pacote.

Em ambos os casos, você precisará procurar uma pasta ou entrada em [nuget.org](https://www.nuget.org/) com um dos seguintes nomes:

```
netstandard1.0
netstandard1.1
netstandard1.2
netstandard1.3
netstandard1.4
netstandard1.5
netstandard1.6
netcoreapp1.0
portable-net45-win8
portable-win8-wpa8
portable-net451-win81
portable-net45-win8-wpa8-wpa81
```

Esses são TFMs (Monikers da Estrutura de Destino), que são mapeados para versões do [.NET Standard](../../standard/net-standard.md) e perfis de PCL (Biblioteca de Classes Portátil) tradicionais, os quais são compatíveis com .NET Core.  Observe que `netcoreapp1.0`, embora seja compatível, ele se destina a aplicativos e não a bibliotecas.  Embora não haja nada de errado em usar uma biblioteca baseada em `netcoreapp1.0`, ela pode não destinar-se a nada *além* de consumir outros aplicativos `netcoreapp1.0`.

Também há alguns TFMs herdados usados em versões de pré-lançamento do .NET Core que podem ser compatíveis:

```
dnxcore50
dotnet5.0
dotnet5.1
dotnet5.2
dotnet5.3
dotnet5.4
dotnet5.5
```

**Embora elas provavelmente funcionarão com o seu código, não há nenhuma garantia de compatibilidade**.  Pacotes com esses TFMs foram compilados com pacotes de pré-lançamento do .NET Core.  Tome nota de quando (se ocorrer) tais pacotes forem atualizados para serem baseados em `netstandard`.

> [!NOTE]
> Para usar um pacote direcionado para uma PCL tradicional ou para um destino .NET Core pré-lançamento, você deve usar a diretiva `imports` no seu arquivo `project.json`.

### <a name="what-to-do-when-your-nuget-package-dependency-doesnt-run-on-net-core"></a>O que fazer quando a dependência de pacote NuGet não é executada no .NET Core

Há algumas coisas que você pode fazer se um pacote NuGet do qual você depende não for executado no .NET Core.

1. Se o projeto for um software livre e estiver hospedados em algum lugar como o GitHub, você poderá entrar em contato com os desenvolvedores diretamente.
2. Você pode contatar o autor diretamente em [nuget.org](https://www.nuget.org/) procurando o pacote e clicando em "Entre em contato com os proprietários" no lado esquerdo da página do pacote.
3. Você pode procurar por outro pacote que é executado no .NET Core que realiza a mesma tarefa do pacote que você estava usando.
4. Você pode tentar escrever por conta própria o código do que o pacote estava fazendo.
5. Você pode eliminar a dependência do pacote alterando a funcionalidade do aplicativo, pelo menos até que uma versão compatível do pacote fique disponível.

Lembre-se que mantenedores do projeto de software livre e editores de pacotes NuGet costumam ser voluntários que contribuem porque se importam com um determinado domínio, fazendo-o gratuitamente e geralmente têm um emprego regular diferente. Se você entrar em contato, introduza uma declaração positiva sobre a biblioteca antes de pedir suporte para o .NET Core.

Se você não conseguir resolver seu problema com nenhuma das opções acima, talvez seja necessário realizar a portabilidade para o .NET Core posteriormente.

A Equipe .NET gostaria de saber quais bibliotecas são as próximas mais importantes para receber suporte no .NET Core. Você também pode nos enviar um email em dotnet@microsoft.com sobre as bibliotecas que você deseja usar.

## <a name="analyzing-dependencies-which-arent-nuget-packages"></a>Analisando dependências que não são pacotes NuGet

Você pode ter uma dependência que não é um pacote NuGet, tal como uma DLL no sistema de arquivos.  A única maneira de determinar a portabilidade dessa dependência é executar a [ferramenta ApiPort](https://github.com/Microsoft/dotnet-apiport/blob/master/docs/HowTo/).

## <a name="next-steps"></a>Próximas etapas

Se você estiver portando uma biblioteca, consulte [Portando suas bibliotecas](libraries.md).
