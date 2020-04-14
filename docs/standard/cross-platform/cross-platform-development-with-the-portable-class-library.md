---
title: Desenvolvimento entre plataformas com a Biblioteca de Classes Portátil
ms.date: 09/17/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- Portable Class Library [.NET Framework]
- targeting multiple platforms
- multiple platforms, targeting
ms.assetid: c31e1663-c164-4e65-b66d-d3aa8750a154
ms.openlocfilehash: 7caddd7361b8f364762fb4357e35cb918ae99263
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242797"
---
# <a name="cross-platform-development-with-the-portable-class-library"></a>Desenvolvimento multiplataforma com a Biblioteca de Classes Portáteis

O tipo de projeto da Biblioteca de Classe Portátil no Visual Studio ajuda você a construir aplicativos e bibliotecas multiplataforma para plataformas Microsoft de forma rápida e fácil.

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

Bibliotecas de classes portáteis podem ajudar a reduzir o tempo e os custos com desenvolvimento e testes de código. Use esse tipo de projeto para escrever e construir conjuntos de estruturas .NET portáteis e, em seguida, faça referência a esses conjuntos de aplicativos que visam várias plataformas, como o .NET Framework, iOS ou Mac.

Mesmo depois de criar um projeto de Biblioteca de Classes Portátil no Visual Studio e começar a desenvolvê-lo, é possível alterar as plataformas de destino. O Visual Studio compila sua biblioteca com os novos conjuntos, o que ajuda você a identificar as alterações que você precisa fazer em seu código.

## <a name="create-a-portable-class-library-project"></a>Crie um projeto de biblioteca de classes portáteis

Para criar uma Biblioteca de Classes Portáteis, use o modelo fornecido no Visual Studio. Crie um novo projeto (**File** > **New Project**), e na caixa de diálogo Novo **Projeto,** selecione sua linguagem de programação (Visual C# ou Visual Basic). Em seguida, selecione o modelo Biblioteca de classe **(Legacy Portable).** Digite um nome para o seu projeto e escolha **OK**.

A caixa de diálogo **Adicionar biblioteca de classe portátil** é exibida. Escolha dois ou mais alvos e escolha **OK**.

![Adicionar alvos de biblioteca de classe portáteis no Visual Studio](media/add-portable-class-library.png)

## <a name="change-targets"></a>Alterar metas

Você pode alterar as plataformas-alvo de um projeto de biblioteca de classe portátil quando você criá-lo ou depois de ter iniciado o desenvolvimento. Se você quiser alterar os alvos depois de criar seu projeto, no **Solution Explorer,** abra o menu de atalho para o projeto da Biblioteca de Classe Portátil (não a solução) e escolha **Propriedades**. Na página propriedades do projeto, a guia **Biblioteca** mostra as plataformas que seu projeto tem como alvo atualmente.

![Propriedades do projeto para biblioteca de classe portátil no Visual Studio](media/pcl-project-properties.png)

Para adicionar ou remover alvos, escolha o botão **Alterar** e, em seguida, selecione e limpe as caixas de seleção apropriadas.

Ao alterar os destinos, as APIs disponíveis para desenvolver o projeto mudarão conforme a sua seleção. O Visual Studio relata os erros e avisos que podem ocorrer como resultado de alterações nos destinos.

Se você quiser avaliar a portabilidade de seus conjuntos antes de fazer alterações no Visual Studio, você pode usar o [Analisador de Portabilidade .NET](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer).

## <a name="supported-types-and-members"></a>Tipos e membros com suporte

Os tipos e membros disponíveis em projetos da Biblioteca de Classes Portátil são restritos por vários fatores de compatibilidade:

- Eles devem ser compartilhados entre os destinos selecionados.

- Eles devem se comportar de forma semelhante nesses destinos.

- Eles não devem ser candidatos à substituição.

- Eles devem fazer sentido em um ambiente portátil, especialmente quando os membros de suporte não são portáveis.

Se houver suporte a um membro na Biblioteca de Classes Portátil e aos destinos selecionados, isso aparecerá no projeto no IntelliSense. Porém, lembre-se de que uma API pode ter suporte na Biblioteca de Classes Portátil, mas sua capacidade de usá-la dependerá dos destinos selecionados.

## <a name="api-differences-in-the-portable-class-library"></a>Diferenças de API na Biblioteca de Classes Portátil

Para tornar os assemblies da Biblioteca de Classes Portátil compatíveis entre todas as plataformas com suporte, alguns membros foram ligeiramente alterados na Biblioteca de Classes Portátil.

## <a name="use-the-portable-class-library"></a>Use a Biblioteca de Classes Portáteis

Depois de criar o projeto da Biblioteca de Classes Portátil, você simplesmente faz uma referência a ele em outros projetos. Você pode fazer referência ao projeto ou assemblies específicos que contêm as classes que deseja acessar.

Para executar um aplicativo que faça referência a um assembly da Biblioteca de Classes Portátil, deve ser instalada a versão necessária (ou uma versão posterior) das plataformas de destino no computador. O Visual Studio contém todas as estruturas necessárias, assim, você pode executar aplicativos sem alteração adicional no computador usado para desenvolver o aplicativo.

### <a name="deploy-a-universal-windows-app"></a>Implantar um aplicativo Universal Windows

Quando você cria um aplicativo Universal Windows que faz referência a um conjunto de Biblioteca de Classe Portátil, tudo o que você precisa para implantar o aplicativo está incluído no pacote do aplicativo, e não são necessárias mais etapas.

### <a name="deploy-a-net-framework-app"></a>Implantar um aplicativo .NET Framework

Ao implantar o aplicativo do .NET Framework que faça referência a um assembly da Biblioteca de Classes Portátil, você deve especificar uma dependência na versão correta do .NET Framework. Ao especificar essa dependência, você garante que a versão requisitada seja instalada com seu aplicativo.

- Para criar uma dependência com a implantação do ClickOnce: No **Solution Explorer,** escolha o nó do projeto para o projeto que deseja publicar. (Este é o projeto que faz referência ao projeto Biblioteca de Classes Portáteis.) Na barra de menu, escolha**Propriedades do** **projeto** > e escolha a guia **Publicar.** Na página **Publicar,** escolha **Pré-requisitos**. Selecione a versão necessária do .NET Framework como um pré-requisito.

- Para criar uma dependência com um projeto de configuração: No **Solution Explorer,** escolha o projeto de configuração. Na barra de menus, **escolha** > **pré-requisitos de****propriedades** > do projeto . Selecione a versão necessária do .NET Framework como um pré-requisito.

Para obter mais informações sobre a implantação de aplicativos .NET Framework, consulte [Guia de implantação para desenvolvedores](../../../docs/framework/deployment/deployment-guide-for-developers.md).

## <a name="see-also"></a>Confira também

- [Usando a Biblioteca de Classes Portátil com o Modelo MVVM](using-portable-class-library-with-model-view-view-model.md)
- [Recursos de aplicativos para bibliotecas que visam várias plataformas](app-resources-for-libraries-that-target-multiple-platforms.md)
- [.NET Portability Analyzer](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)
- [Suporte do .NET Framework para Aplicativos da Windows Store e Windows Runtime](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
- [Implantação](../../../docs/framework/deployment/net-framework-applications.md)
