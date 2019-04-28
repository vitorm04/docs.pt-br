---
title: Habilitar ou desabilitar os redirecionamentos de associação geradas automaticamente
ms.date: 10/30/2018
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 5fca42f3-bdce-4b81-a704-61e42c89d3ba
ms.openlocfilehash: f646445d5fa4556646700bb5daf8ac859631da2c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61880096"
---
# <a name="how-to-enable-and-disable-automatic-binding-redirection"></a>Como: Habilitar e desabilitar o redirecionamento automático de associação

Quando você compila aplicativos no Visual Studio que se destinam a [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] e versões posteriores, redirecionamentos de associação poderão ser automaticamente adicionadas ao arquivo de configuração de aplicativo para substituir a Unificação do assembly. Redirecionamentos de associação serão adicionados se o seu aplicativo ou seus componentes fizerem referência a mais de uma versão do mesmo assembly, mesmo se você especificar manualmente redirecionamentos de associação no arquivo de configuração para seu aplicativo. O recurso de redirecionamento de associação automático afeta os aplicativos da área de trabalho e aplicativos web que se destinam a [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] ou uma versão posterior, embora o comportamento é ligeiramente diferente para um aplicativo web. Você pode habilitar o redirecionamento de associação automático se você tiver aplicativos existentes destinados a versões anteriores do .NET Framework, ou você pode desativar esse recurso se você quiser criar manualmente redirecionamentos de associação.

## <a name="disable-automatic-binding-redirects-in-desktop-apps"></a>Desabilitar os redirecionamentos de associação automáticos em aplicativos da área de trabalho

Redirecionamentos de associação automáticos são habilitados por padrão para aplicativos de desktop do Windows que se destinam a [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] e versões posteriores. Os redirecionamentos de associação são adicionados à configuração de saída (**App. config**) de arquivos quando o aplicativo é compilado e substituem a Unificação do assembly que pode ocorrer de outra forma. O código-fonte **App. config** arquivo não é modificado. Modificando o arquivo de projeto para o aplicativo ou desmarcar uma caixa de seleção nas propriedades do projeto no Visual Studio, você pode desativar esse recurso.

### <a name="disable-through-project-properties"></a>Desabilitar por meio das propriedades do projeto

Se você tiver o Visual Studio 2017 versão 15.7 ou posterior, você pode desativar com facilidade os redirecionamentos de associação geradas automaticamente nas páginas de propriedades do projeto.

1. Clique com o botão direito do mouse no projeto no **Gerenciador de Soluções** e selecione **Propriedades**.

2. Sobre o **aplicativo** página, desmarque a opção a **gerar automaticamente redirecionamentos de associação** opção.

3. Pressione **Ctrl**+**S** para salvar a alteração.

### <a name="disable-manually-in-the-project-file"></a>Desabilitar manualmente no arquivo de projeto

1. Abra o arquivo de projeto para edição usando um dos seguintes métodos:

   - No Visual Studio, selecione o projeto no **Gerenciador de soluções**e, em seguida, escolha **Abrir pasta no Explorador de arquivos** no menu de atalho. No Explorador de arquivos, localize o arquivo de projeto (. csproj ou. vbproj) e abri-lo no bloco de notas.
   - No Visual Studio, no **Gerenciador de soluções**, clique com botão direito no projeto e escolha **descarregar projeto**. Clique com botão direito do projeto descarregado novamente e, em seguida, escolha **Editar [projectname.csproj]**.

2. No arquivo de projeto, localize a seguinte entrada de propriedade:

   ```xml
   <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>
   ```

3. Altere `true` para `false`:

   ```xml
   <AutoGenerateBindingRedirects>false</AutoGenerateBindingRedirects>
   ```

## <a name="enable-automatic-binding-redirects-manually"></a>Habilitar redirecionamentos de associação automáticos manualmente

Você pode habilitar redirecionamentos de associação automáticos em aplicativos existentes destinados a versões anteriores do .NET Framework, ou em casos em que você é automaticamente solicitado a adicionar um redirecionamento. Se você estiver visando uma versão mais recente do framework, mas não solicitar automaticamente a adição de um redirecionamento, você provavelmente obterá saída de compilação que solicitará o remapeamento assemblies.

1. Abra o arquivo de projeto para edição usando um dos seguintes métodos:

   - No Visual Studio, selecione o projeto no **Gerenciador de soluções**e, em seguida, escolha **Abrir pasta no Explorador de arquivos** no menu de atalho. No Explorador de arquivos, localize o arquivo de projeto (. csproj ou. vbproj) e abri-lo no bloco de notas.
   - No Visual Studio, no **Gerenciador de soluções**, clique com botão direito no projeto e escolha **descarregar projeto**. Clique com botão direito do projeto descarregado novamente e, em seguida, escolha **Editar [projectname.csproj]**.

2. Adicione o seguinte elemento ao primeiro grupo de propriedades de configuração (sob o \<PropertyGroup > marca):

   ```xml
   <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>
   ```

   A seguir mostra um exemplo de arquivo de projeto com o elemento inserido:

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <Project ToolsVersion="12.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
     <Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props" Condition="Exists('$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props')" />
       <PropertyGroup>
         <Configuration Condition=" '$(Configuration)' == ''     ">Debug</Configuration>
         <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>
         <ProjectGuid>{123334}</ProjectGuid>
         ...
         <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>
       </PropertyGroup>
     ...
   </Project>
   ```

3. Compile seu aplicativo.

## <a name="enable-automatic-binding-redirects-in-web-apps"></a>Habilitar redirecionamentos de associação automáticos em aplicativos web

Redirecionamentos de associação automáticos são implementados de maneira diferente para aplicativos Web. Porque a configuração de origem (**Web. config**) arquivo deve ser modificado para aplicativos web, redirecionamentos de associação não são automaticamente adicionados ao arquivo de configuração. Entretanto, o Visual Studio o notifica sobre conflitos de associação e você pode adicionar redirecionamentos de associação para resolver os conflitos. Como sempre, você será solicitado a adicionar redirecionamentos de associação, você não precisa desabilitar explicitamente esse recurso para um aplicativo web.

Para adicionar redirecionamentos de associação para um **Web. config** arquivo:

1. No Visual Studio, compile o aplicativo e verifique a existência de avisos de compilação.

   ![Aviso para conflitos de referência de assembly de compilação](../../../docs/framework/configure-apps/media/clr-assemblyrefwarning.png "CLR_AssemblyRefWarning")

2. Se houver conflitos de associação de assembly, um aviso será exibido. Clique duas vezes no aviso, ou selecione o aviso e pressione **Enter**.

   Caixa de diálogo que permite que você adicione automaticamente a associação necessário redireciona para a fonte **Web. config** arquivo aparece.

   ![Caixa de diálogo de permissão de redirecionamento de associação](../../../docs/framework/configure-apps/media/clr-addbindingredirect.png "CLR_AddBindingRedirect")

## <a name="see-also"></a>Consulte também

- [\<bindingRedirect > elemento](../../../docs/framework/configure-apps/file-schema/runtime/bindingredirect-element.md)
- [Redirecionando versões de assembly](../../../docs/framework/configure-apps/redirect-assembly-versions.md)
