---
title: Como habilitar e desabilitar o redirecionamento automático de associações
ms.date: 09/12/2018
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 5fca42f3-bdce-4b81-a704-61e42c89d3ba
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 9b9c9cbdb89ccf67942dcccee37ea410c6fa39a5
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47208666"
---
# <a name="how-to-enable-and-disable-automatic-binding-redirection"></a>Como habilitar e desabilitar o redirecionamento automático de associações

Quando você compila aplicativos no Visual Studio que se destinam a [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] e versões posteriores, redirecionamentos de associação poderão ser automaticamente adicionadas ao arquivo de configuração de aplicativo para substituir a Unificação do assembly. Redirecionamentos de associação serão adicionados se o seu aplicativo ou seus componentes fizerem referência a mais de uma versão do mesmo assembly, mesmo se você especificar manualmente redirecionamentos de associação no arquivo de configuração para seu aplicativo. O recurso de redirecionamento de associação automático afeta aplicativos de desktop tradicionais e aplicativos web que se destinam a [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] ou uma versão posterior, embora o comportamento é ligeiramente diferente para um aplicativo web. Você pode habilitar o redirecionamento de associação automático se houver aplicativos que usem versões anteriores do .NET Framework ou pode desativar esse recurso se desejar manter redirecionamentos manuais de associações criadas.

## <a name="disable-automatic-binding-redirects-in-desktop-apps"></a>Desabilitar os redirecionamentos de associação automáticos em aplicativos da área de trabalho

Os redirecionamentos de associação automáticos são habilitados por padrão para aplicativos tradicionais da área de trabalho que usam o [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] e versões posteriores. Os redirecionamentos de associação são adicionadas ao arquivo de configuração de saída (app.config) quando o aplicativo é compilado e substituem a unificação do assembly que pode ocorrer de outra forma. O arquivo de origem app.config não é modificado. Você pode desativar esse recurso ao modificar o arquivo de projeto para o aplicativo.

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

Redirecionamentos de associação automáticos são implementados de maneira diferente para aplicativos Web. Como o arquivo de configuração de origem (web.config) deve ser modificado para aplicativos Web, redirecionamentos de associação não são adicionados automaticamente ao arquivo de configuração. Entretanto, o Visual Studio o notifica sobre conflitos de associação e você pode adicionar redirecionamentos de associação para resolver os conflitos. Como sempre, você será solicitado a adicionar redirecionamentos de associação, você não precisa desabilitar explicitamente esse recurso para um aplicativo web.

Para adicionar redirecionamentos de associação a um arquivo Web. config:

1. No Visual Studio, compile o aplicativo e verifique a existência de avisos de compilação.

   ![Aviso para conflitos de referência de assembly de compilação](../../../docs/framework/configure-apps/media/clr-assemblyrefwarning.png "CLR_AssemblyRefWarning")

2. Se houver conflitos de associação de assembly, um aviso será exibido. Clique duas vezes no aviso, ou selecione o aviso e pressione **Enter**.

   Uma caixa de diálogo que permite adicionar automaticamente os redirecionamentos da associação necessários ao arquivo web.config de origem é exibida.

   ![Caixa de diálogo de permissão de redirecionamento de associação](../../../docs/framework/configure-apps/media/clr-addbindingredirect.png "CLR_AddBindingRedirect")

## <a name="see-also"></a>Consulte também

- [\<bindingRedirect > elemento](../../../docs/framework/configure-apps/file-schema/runtime/bindingredirect-element.md)
- [Redirecionando versões de assembly](../../../docs/framework/configure-apps/redirect-assembly-versions.md)
