---
title: Aparar aplicações independentes
description: Aprenda a aparar aplicativos autônomos para reduzir seu tamanho. O .NET Core empacota o tempo de execução com um aplicativo que é publicado independente mente e geralmente inclui mais tempo de execução do que é necessário.
author: jamshedd
ms.author: jamshedd
ms.date: 04/03/2020
ms.openlocfilehash: bb8ac88c5e16b7fd20a7670e4ad76dbe4b44da1b
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242888"
---
# <a name="trim-self-contained-deployments-and-executables"></a>Cortar implantações e executáveis autossuficientes

Ao publicar um aplicativo independente, o tempo de execução do .NET Core é empacotado com o aplicativo. Este agrupamento adiciona uma quantidade significativa de conteúdo ao seu aplicativo embalado. Quando se trata de implantar seu aplicativo, o tamanho muitas vezes é um fator importante. Manter o tamanho do aplicativo do pacote o menor possível é tipicamente uma meta para os desenvolvedores de aplicativos.

Dependendo da complexidade do aplicativo, apenas um subconjunto do tempo de execução é necessário para executar o aplicativo. Estas partes não utilizadas do tempo de execução são desnecessárias e podem ser cortadas da aplicação embalada.

O recurso de corte funciona examinando os binários de aplicativos para descobrir e construir um gráfico dos conjuntos de tempo de execução necessários. As demais assembléias de tempo de execução que não são referenciadas são excluídas.

> [!NOTE]
> Trimming é um recurso experimental no .NET Core 3.1 e _só_ está disponível para aplicativos que são publicados independentes.

## <a name="prevent-assemblies-from-being-trimmed"></a>Evitar que as assembléias sejam aparadas

Existem cenários em que a funcionalidade de corte falhará em detectar referências. Por exemplo, quando a reflexão é usada em um conjunto de tempo de execução, seja por sua aplicação ou por uma biblioteca referenciada pelo seu aplicativo, o conjunto não é diretamente referenciado. O corte desconhece essas referências indiretas e excluiria a biblioteca da pasta publicada.

Quando o código está indiretamente referenciando uma montagem através da reflexão, você pode impedir que a montagem seja aparada com a configuração. `<TrimmerRootAssembly>` O exemplo a seguir mostra `System.Security` como evitar que uma assembléia chamada montagem seja aparada:

```xml
<ItemGroup>
    <TrimmerRootAssembly Include="System.Security" />
</ItemGroup>
```

## <a name="trim-your-app---cli"></a>Apare seu aplicativo - CLI

Corte sua aplicação usando o comando [dotnet publish.](../tools/dotnet-publish.md) Ao publicar seu aplicativo, defina as três configurações a seguir:

- Publicar como autônomo:`--self-contained true`
- Desativar a publicação de arquivos únicos:`-p:PublishSingleFile=false`
- Habilite o corte:`p:PublishTrimmed=true`

O exemplo a seguir publica um aplicativo para windows 10 como autônomo e apara a saída.

```dotnetcli
dotnet publish -c Release -r win10-x64 --self-contained true -p:PublishSingleFile=false -p:PublishTrimmed=true
```

Para obter mais informações, consulte [Publicar os aplicativos .NET Core com .NET Core CLI](deploy-with-cli.md).

## <a name="trim-your-app---visual-studio"></a>Apare seu aplicativo - Visual Studio

O Visual Studio cria perfis de publicação reutilizáveis que controlam como seu aplicativo é publicado.

01. No **painel Solution Explorer,** clique com o botão direito do mouse sobre o projeto que deseja publicar. Selecione **Publicar...**.

    :::image type="content" source="media/trim-self-contained/visual-studio-solution-explorer.png" alt-text="Solution Explorer com um menu com o botão direito do mouse destacando a opção Publicar.":::

    Se você ainda não tiver um perfil de publicação, siga as instruções para criar um e escolha o tipo de destino **pasta.**

01. Escolha **Editar**.

    :::image type="content" source="media/trim-self-contained/visual-studio-publish-edit-settings.png" alt-text="Visual studio publicar perfil com botão de edição.":::

01. Na caixa de diálogo **Configurações de** perfil, defina as seguintes opções:

    - Defina **o modo de implantação** como **autônomo**.
    - Defina **o tempo de execução do Target** para a plataforma para a a que deseja publicar.
    - Selecione **Trim conjuntos não utilizados (na visualização)**.

    Escolha **Salvar** para salvar as configurações e retornar à caixa de diálogo **Publicar.**

    :::image type="content" source="media/trim-self-contained/visual-studio-publish-properties.png" alt-text="As configurações do perfil dialogam com o modo de implantação, o tempo de execução do destino e as opções de montagem não utilizadas destacadas.":::

01. Escolha **Publicar** para publicar seu aplicativo aparado.

Para obter mais informações, consulte [Publicar os aplicativos .NET Core com o Visual Studio](deploy-with-vs.md).

## <a name="trim-your-app---visual-studio-for-mac"></a>Apare seu aplicativo - Visual Studio para Mac

Visual Studio para Mac não oferece opções para aparar seu aplicativo durante a publicação. Você precisará publicar manualmente seguindo as instruções da [seção Trim your app - CLI.](#trim-your-app---cli) Para obter mais informações, consulte [Publicar os aplicativos .NET Core com .NET Core CLI](deploy-with-cli.md).

## <a name="see-also"></a>Confira também

- [Implantação de aplicativo .NET Core](index.md).
- [Publique os aplicativos .NET Core com .NET Core CLI](deploy-with-cli.md).
- [Publique os aplicativos .NET Core com o Visual Studio](deploy-with-vs.md).
- [comando dotnet publicar](../tools/dotnet-publish.md).
