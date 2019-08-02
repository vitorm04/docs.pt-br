---
title: Habilitar ou desabilitar redirecionamentos de associação gerados automaticamente
ms.date: 10/30/2018
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 5fca42f3-bdce-4b81-a704-61e42c89d3ba
ms.openlocfilehash: d914310559403fba2f1fe8e4a60469ec3a867c24
ms.sourcegitcommit: 8c6426a3d2adff5fbcbe1fed0f28eda718c15351
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/02/2019
ms.locfileid: "68733446"
---
# <a name="how-to-enable-and-disable-automatic-binding-redirection"></a>Como: Habilitar e desabilitar o redirecionamento automático de associação

Quando você compila aplicativos no Visual Studio destinados ao .NET Framework 4.5.1 e versões posteriores, os redirecionamentos de associação podem ser adicionados automaticamente ao arquivo de configuração do aplicativo para substituir a unificação do assembly. Redirecionamentos de associação serão adicionados se o seu aplicativo ou seus componentes fizerem referência a mais de uma versão do mesmo assembly, mesmo se você especificar manualmente redirecionamentos de associação no arquivo de configuração para seu aplicativo. O recurso de redirecionamento de associação automática afeta aplicativos da área de trabalho e aplicativos Web direcionados para o .NET Framework 4.5.1 ou uma versão posterior, embora o comportamento seja um pouco diferente para um aplicativo Web. Você pode habilitar o redirecionamento de associação automática se tiver aplicativos que se destinam a versões anteriores do .NET Framework, ou pode desabilitar esse recurso se desejar criar manualmente os redirecionamentos de associação.

## <a name="disable-automatic-binding-redirects-in-desktop-apps"></a>Desabilitar redirecionamentos de associação automática em aplicativos da área de trabalho

Os redirecionamentos de associação automática são habilitados por padrão para aplicativos de área de trabalho do Windows direcionados para o .NET Framework 4.5.1 e versões posteriores. Os redirecionamentos de associação são adicionados ao arquivo de configuração de saída (**app. config**) quando o aplicativo é compilado e substituem a Unificação de assembly que, de outra forma, poderia ocorrer. O arquivo **app. config** de origem não é modificado. Você pode desabilitar esse recurso modificando o arquivo de projeto do aplicativo ou desmarcando uma caixa de seleção nas propriedades do projeto no Visual Studio.

### <a name="disable-through-project-properties"></a>Desabilitar por meio de propriedades do projeto

Se você tiver o Visual Studio 2017 versão 15,7 ou posterior, poderá desabilitar facilmente os redirecionamentos de associação gerados automaticamente nas páginas de propriedades do projeto.

1. Clique com o botão direito do mouse no projeto no **Gerenciador de Soluções** e selecione **Propriedades**.

2. Na página do **aplicativo** , desmarque a opção gerar redirecionamentos de **Associação automaticamente** .

3. Pressione **Ctrl**+**S** para salvar a alteração.

### <a name="disable-manually-in-the-project-file"></a>Desabilitar manualmente no arquivo de projeto

1. Abra o arquivo de projeto para edição usando um dos seguintes métodos:

   - No Visual Studio, selecione o projeto em **Gerenciador de soluções**e, em seguida, escolha **abrir pasta no explorador de arquivos** no menu de atalho. No explorador de arquivos, localize o arquivo de projeto (. csproj ou. vbproj) e abra-o no bloco de notas.
   - No Visual Studio, em **Gerenciador de soluções**, clique com o botão direito do mouse no projeto e escolha **descarregar projeto**. Clique com o botão direito do mouse no projeto descarregado e escolha **Editar [ProjectName. csproj]** .

2. No arquivo de projeto, localize a seguinte entrada de propriedade:

   ```xml
   <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>
   ```

3. Altere `true` para `false`:

   ```xml
   <AutoGenerateBindingRedirects>false</AutoGenerateBindingRedirects>
   ```

## <a name="enable-automatic-binding-redirects-manually"></a>Habilitar redirecionamentos de associação automática manualmente

Você pode habilitar redirecionamentos de associação automática em aplicativos existentes direcionados a versões mais antigas do .NET Framework, ou em casos em que não seja solicitado automaticamente a adicionar um redirecionamento. Se você estiver direcionando para uma versão mais recente da estrutura, mas não for solicitado automaticamente a adicionar um redirecionamento, provavelmente obterá uma saída de compilação que sugere os assemblies de remapeamento.

1. Abra o arquivo de projeto para edição usando um dos seguintes métodos:

   - No Visual Studio, selecione o projeto em **Gerenciador de soluções**e, em seguida, escolha **abrir pasta no explorador de arquivos** no menu de atalho. No explorador de arquivos, localize o arquivo de projeto (. csproj ou. vbproj) e abra-o no bloco de notas.
   - No Visual Studio, em **Gerenciador de soluções**, clique com o botão direito do mouse no projeto e escolha **descarregar projeto**. Clique com o botão direito do mouse no projeto descarregado e escolha **Editar [ProjectName. csproj]** .

2. Adicione o seguinte elemento ao primeiro grupo de propriedades de configuração (sob \<a marca de > PropertyGroup):

   ```xml
   <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>
   ```

   Veja a seguir um exemplo de arquivo de projeto com o elemento inserido:

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <Project ToolsVersion="12.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
     <Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props" Condition="Exists('$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props')" />
     <PropertyGroup>
       <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>
       <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>
       <ProjectGuid>{123334}</ProjectGuid>
       ...
       <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>
     </PropertyGroup>
     ...
   </Project>
   ```

3. Compile seu aplicativo.

## <a name="enable-automatic-binding-redirects-in-web-apps"></a>Habilitar redirecionamentos de associação automática em aplicativos Web

Redirecionamentos de associação automáticos são implementados de maneira diferente para aplicativos Web. Como o arquivo de configuração de origem (**Web. config**) deve ser modificado para aplicativos Web, os redirecionamentos de associação não são adicionados automaticamente ao arquivo de configuração. Entretanto, o Visual Studio o notifica sobre conflitos de associação e você pode adicionar redirecionamentos de associação para resolver os conflitos. Como você sempre é solicitado a adicionar redirecionamentos de associação, não é necessário desabilitar explicitamente esse recurso para um aplicativo Web.

Para adicionar redirecionamentos de associação a um arquivo **Web. config** :

1. No Visual Studio, compile o aplicativo e verifique a existência de avisos de compilação.

   ![Aviso de compilação para conflitos de referência de assembly](../../../docs/framework/configure-apps/media/clr-assemblyrefwarning.png "CLR_AssemblyRefWarning")

2. Se houver conflitos de associação de assembly, um aviso será exibido. Clique duas vezes no aviso ou selecione o aviso e pressione **Enter**.

   Uma caixa de diálogo que permite adicionar automaticamente os redirecionamentos de associação necessários ao arquivo **Web. config** de origem é exibida.

   ![Diálogo de permissão] de redirecionamento de associação (../../../docs/framework/configure-apps/media/clr-addbindingredirect.png "CLR_AddBindingRedirect")

## <a name="see-also"></a>Consulte também

- [\<Elemento > bindingRedirect](../../../docs/framework/configure-apps/file-schema/runtime/bindingredirect-element.md)
- [Redirecionando versões de assembly](../../../docs/framework/configure-apps/redirect-assembly-versions.md)
