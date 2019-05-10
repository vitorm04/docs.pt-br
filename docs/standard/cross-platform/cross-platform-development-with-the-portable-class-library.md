---
title: Desenvolvimento entre plataformas com a Biblioteca de Classes Portátil
ms.date: 09/17/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- Portable Class Library [.NET Framework]
- targeting multiple platforms
- multiple platforms, targeting
ms.assetid: c31e1663-c164-4e65-b66d-d3aa8750a154
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e5b6a32aa465700fb316bf2269c4d057ff823443
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64590342"
---
# <a name="cross-platform-development-with-the-portable-class-library"></a>Desenvolvimento de plataforma cruzada com a biblioteca de classes portátil

O tipo de projeto de biblioteca de classes portátil no Visual Studio ajuda a criar aplicativos de plataforma cruzada e bibliotecas para plataformas da Microsoft de forma rápida e fácil.

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

Bibliotecas de classes portáteis podem ajudar a reduzir o tempo e os custos com desenvolvimento e testes de código. Use esse tipo de projeto para gravar e compilar assemblies .NET Framework portáteis e, em seguida, referenciar os assemblies de aplicativos destinados a várias plataformas, como o .NET Framework, iOS ou Mac.

Mesmo depois de criar um projeto de Biblioteca de Classes Portátil no Visual Studio e começar a desenvolvê-lo, é possível alterar as plataformas de destino. O Visual Studio compila sua biblioteca com os novos assemblies, que ajuda você a identificar as alterações que você precisa fazer em seu código.

## <a name="create-a-portable-class-library-project"></a>Criar um projeto de biblioteca de classes portátil

Para criar uma biblioteca de classes portátil, use o modelo fornecido no Visual Studio. Criar um novo projeto (**arquivo** > **novo projeto**) e, no **novo projeto** caixa de diálogo, selecione a linguagem de programação (Visual c# ou Visual Basic). Em seguida, selecione a **biblioteca de classes (portátil herdado)** modelo. Insira um nome para seu projeto e escolha **Okey**.

O **adicionar a biblioteca de classes portátil** caixa de diálogo é exibida. Escolha dois ou mais destinos e, em seguida, escolha **Okey**.

![Adicionar destinos da biblioteca de classes portátil no Visual Studio](media/add-portable-class-library.png)

## <a name="change-targets"></a>Alterar destinos

Quando você criá-lo ou depois de começar o desenvolvimento, você pode alterar as plataformas de destino de um projeto de biblioteca de classes portátil. Se você quiser alterar os destinos depois de criar seu projeto, no **Gerenciador de soluções**, abra o menu de atalho para o seu projeto de biblioteca de classes portátil (não na solução) e, em seguida, escolha **propriedades** . Na página de propriedades de projeto, o **biblioteca** guia mostra as plataformas que o projeto está destinado atualmente.

![Propriedades do projeto de biblioteca de classes portátil no Visual Studio](media/pcl-project-properties.png)

Para adicionar ou remover destinos, escolha o **alteração** botão e, em seguida, selecione e desmarque as caixas de seleção apropriadas.

Ao alterar os destinos, as APIs disponíveis para desenvolver o projeto mudarão conforme a sua seleção. O Visual Studio relata os erros e avisos que podem ocorrer como resultado de alterações nos destinos.

Se você quiser avaliar a portabilidade de seus assemblies antes de fazer alterações no Visual Studio, você pode usar o [.NET Portability Analyzer](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b).

## <a name="supported-types-and-members"></a>Tipos e membros com suporte

Os tipos e membros disponíveis em projetos da Biblioteca de Classes Portátil são restritos por vários fatores de compatibilidade:

- Eles devem ser compartilhados entre os destinos selecionados.

- Eles devem se comportar de forma semelhante nesses destinos.

- Eles não devem ser candidatos à substituição.

- Eles devem fazer sentido em um ambiente portátil, especialmente quando os membros de suporte não são portáveis.

Se houver suporte a um membro na Biblioteca de Classes Portátil e aos destinos selecionados, isso aparecerá no projeto no IntelliSense. Porém, lembre-se de que uma API pode ter suporte na Biblioteca de Classes Portátil, mas sua capacidade de usá-la dependerá dos destinos selecionados.

## <a name="api-differences-in-the-portable-class-library"></a>Diferenças de API na Biblioteca de Classes Portátil

Para tornar os assemblies da Biblioteca de Classes Portátil compatíveis entre todas as plataformas com suporte, alguns membros foram ligeiramente alterados na Biblioteca de Classes Portátil.

## <a name="use-the-portable-class-library"></a>Use a biblioteca de classes portátil

Depois de criar o projeto da Biblioteca de Classes Portátil, você simplesmente faz uma referência a ele em outros projetos. Você pode fazer referência ao projeto ou assemblies específicos que contêm as classes que deseja acessar.

Para executar um aplicativo que faça referência a um assembly da Biblioteca de Classes Portátil, deve ser instalada a versão necessária (ou uma versão posterior) das plataformas de destino no computador. O Visual Studio contém todas as estruturas necessárias, assim, você pode executar aplicativos sem alteração adicional no computador usado para desenvolver o aplicativo.

### <a name="deploy-a-universal-windows-app"></a>Implantar um aplicativo Windows Universal

Quando você cria um aplicativo Windows Universal que referencia um assembly de biblioteca de classes portátil, tudo o que você precisa para implantar o aplicativo está incluído no pacote do aplicativo e nenhuma etapa adicional é necessária.

### <a name="deploy-a-net-framework-app"></a>Implantar um .NET Framework de aplicativo

Ao implantar o aplicativo do .NET Framework que faça referência a um assembly da Biblioteca de Classes Portátil, você deve especificar uma dependência na versão correta do .NET Framework. Ao especificar essa dependência, você garante que a versão requisitada seja instalada com seu aplicativo.

- Para criar uma dependência com a implantação do ClickOnce: Na **Gerenciador de soluções**, escolha o nó do projeto para o projeto que você deseja publicar. (Esse projeto faz referência ao projeto da Biblioteca de Classes Portátil.) Na barra de menus, escolha **Project** > **as propriedades**e, em seguida, escolha o **publicar** guia. Sobre o **Publish** , escolha **pré-requisitos**. Selecione a versão necessária do .NET Framework como um pré-requisito.

- Para criar uma dependência com um projeto de instalação: Na **Gerenciador de soluções**, escolha o projeto de instalação. Na barra de menus, escolha **Project** > **as propriedades** > **pré-requisitos**. Selecione a versão necessária do .NET Framework como um pré-requisito.

Para obter mais informações sobre como implantar aplicativos do .NET Framework, consulte [guia de implantação para os desenvolvedores](../../../docs/framework/deployment/deployment-guide-for-developers.md).

## <a name="see-also"></a>Consulte também

- [Usando a biblioteca de classes portátil com modelo MVVM](../../../docs/standard/cross-platform/using-portable-class-library-with-model-view-view-model.md)
- [Recursos do aplicativo para bibliotecas direcionadas a várias plataformas](../../../docs/standard/cross-platform/app-resources-for-libraries-that-target-multiple-platforms.md)
- [.NET portability Analyzer](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)
- [Suporte do .NET Framework para Aplicativos da Windows Store e Windows Runtime](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
- [Implantação](../../../docs/framework/deployment/net-framework-applications.md)
