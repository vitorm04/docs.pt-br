---
title: Como habilitar e desabilitar o redirecionamento automático de associações
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 5fca42f3-bdce-4b81-a704-61e42c89d3ba
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 2d71da1b48938f9f98221d86f0f9badee3a17919
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32757561"
---
# <a name="how-to-enable-and-disable-automatic-binding-redirection"></a>Como habilitar e desabilitar o redirecionamento automático de associações
A partir do [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)], quando você compila aplicativos destinados ao [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], os redirecionamentos de associação podem ser automaticamente adicionados ao arquivo de configuração do aplicativo para unificação do assembly de substituição. Redirecionamentos de associação serão adicionados se o seu aplicativo ou seus componentes fizerem referência a mais de uma versão do mesmo assembly, mesmo se você especificar manualmente redirecionamentos de associação no arquivo de configuração para seu aplicativo. O recurso de redirecionamento de associação automático afeta os aplicativos tradicionais da área de trabalho que usam o [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], embora o comportamento seja um pouco diferente para um aplicativo Web. Você pode habilitar o redirecionamento de associação automático se houver aplicativos que usem versões anteriores do .NET Framework ou pode desativar esse recurso se desejar manter redirecionamentos manuais de associações criadas.  
  
## <a name="disabling-automatic-binding-redirects-in-desktop-apps"></a>Desabilitando redirecionamentos de associação automáticos em aplicativos da área de trabalho  
 Os redirecionamentos de associação automáticos são habilitados por padrão para aplicativos tradicionais da área de trabalho que usam o [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] e versões posteriores. Os redirecionamentos de associação são adicionadas ao arquivo de configuração de saída (app.config) quando o aplicativo é compilado e substituem a unificação do assembly que pode ocorrer de outra forma. O arquivo de origem app.config não é modificado. Você pode desativar esse recurso ao modificar o arquivo de projeto para o aplicativo.  
  
#### <a name="to-disable-automatic-binding-redirects"></a>Para desativar os redirecionamentos de associação automáticos  
  
1.  No Visual Studio, selecione o projeto em **Solution Explorer**e, em seguida, escolha **Abrir pasta no Explorador de arquivos** no menu de atalho.  
  
2.  No Explorador de Arquivos, localize o arquivo de projeto (.csproj ou .vbproj) e o abra no Bloco de Notas.  
  
3.  No arquivo de projeto, localize a seguinte entrada de propriedade:  
  
     `<AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>`  
  
4.  Altere `true` para `false`:  
  
     `<AutoGenerateBindingRedirects>false</AutoGenerateBindingRedirects>`  
  
## <a name="enabling-automatic-binding-redirects-manually"></a>Habilitando redirecionamentos de associação automáticos manualmente  
 Você pode habilitar redirecionamentos de associação automáticos em aplicativos existentes destinados a versões anteriores do .NET Framework ou caso o sistema não solicite automaticamente a adição de um redirecionamento. Se seu aplicativo for destinado a uma versão mais recente da estrutura, mas o sistema não solicitar automaticamente a adição de um redirecionamento, provavelmente, a saída de compilação solicitará o remapeamento dos assemblies.  
  
#### <a name="to-manually-add-an-automatic-binding-redirect-property"></a>Para adicionar uma propriedade de redirecionamento de associação automático manualmente  
  
1.  No Visual Studio, selecione o projeto em **Solution Explorer**e, em seguida, escolha **Abrir pasta no Explorador de arquivos** no menu de atalho.  
  
2.  No Explorador de Arquivos, localize o arquivo de projeto (.csproj ou .vbproj) e o abra no Bloco de Notas.  
  
3.  Adicione o seguinte elemento para o primeiro grupo de propriedade de configuração (sob o \<PropertyGroup > marca):  
  
     `<AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>`  
  
     O código a seguir mostra um exemplo de arquivo de projeto com o elemento.  
  
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
  
4.  Compile seu aplicativo.  
  
## <a name="enabling-automatic-binding-redirects-in-web-apps"></a>Habilitando redirecionamentos de associação automáticos em aplicativos Web  
 Redirecionamentos de associação automáticos são implementados de maneira diferente para aplicativos Web. Como o arquivo de configuração de origem (web.config) deve ser modificado para aplicativos Web, redirecionamentos de associação não são adicionados automaticamente ao arquivo de configuração. Entretanto, o Visual Studio o notifica sobre conflitos de associação e você pode adicionar redirecionamentos de associação para resolver os conflitos. Como você é sempre solicitado a adicionar redirecionamentos de associação, não é necessário desativar explicitamente esse recurso para um aplicativo Web.  
  
#### <a name="to-add-binding-redirects-to-a-webconfig-file"></a>Para adicionar redirecionamentos de associação a um arquivo web.config  
  
1.  No Visual Studio, compile o aplicativo e verifique a existência de avisos de compilação.  
  
     ![Aviso de conflitos de referência de assembly de compilação](../../../docs/framework/configure-apps/media/clr-assemblyrefwarning.png "CLR_AssemblyRefWarning")  
  
2.  Se houver conflitos de associação de assembly, um aviso será exibido. Clique duas vezes no aviso. (Teclado: selecione o aviso e pressione **Enter**.)  
  
     Uma caixa de diálogo que permite adicionar automaticamente os redirecionamentos da associação necessários ao arquivo web.config de origem é exibida.  
  
     ![Caixa de diálogo de permissões de redirecionamento de associação](../../../docs/framework/configure-apps/media/clr-addbindingredirect.png "CLR_AddBindingRedirect")  
  
## <a name="see-also"></a>Consulte também  
 [\<bindingRedirect > elemento](../../../docs/framework/configure-apps/file-schema/runtime/bindingredirect-element.md)  
 [Redirecionando versões de assembly](../../../docs/framework/configure-apps/redirect-assembly-versions.md)
