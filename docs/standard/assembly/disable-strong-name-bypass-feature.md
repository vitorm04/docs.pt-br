---
title: Como desabilitar o recurso de bypass de nome forte
ms.date: 08/20/2019
helpviewer_keywords:
- strong-name bypass feature
- strong-named assemblies, loading into trusted application domains
ms.assetid: 234e088c-3b11-495a-8817-e0962be79d82
ms.openlocfilehash: a4c4ae7ea61a659d3bede532da3c1bdaea448873
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141108"
---
# <a name="how-to-disable-the-strong-name-bypass-feature"></a>Como desabilitar o recurso de bypass de nome forte
Desde o .NET Framework versão 3.5 Service Pack 1 (SP1), as assinaturas de nome forte não são validadas quando um assembly é carregado em um objeto <xref:System.AppDomain> de confiança total, como o <xref:System.AppDomain> padrão para a zona `MyComputer`. Isso é conhecido como o recurso de desvio de nome forte. Em um ambiente de confiança total, as exigências de <xref:System.Security.Permissions.StrongNameIdentityPermission> sempre têm êxito para assemblies assinados de confiança total, independentemente de sua assinatura. A única restrição é que o assembly deve ser totalmente confiável porque sua zona é totalmente confiável. Como o nome forte não é um fator determinante sob essas condições, não há nenhum motivo para ser validado. Ignorar a validação de assinaturas de nome forte fornece melhorias significativas de desempenho.  
  
 O recurso de desvio se aplica a qualquer assembly de confiança total que não é assinado com atraso e que é carregado em qualquer <xref:System.AppDomain> de confiança total no diretório especificado por sua propriedade <xref:System.AppDomainSetup.ApplicationBase%2A>.  
  
 Você pode substituir o recurso de desvio para todos os aplicativos em um computador definindo um valor de chave do Registro. Você pode substituir a configuração de um único aplicativo usando um arquivo de configuração de aplicativo. Você não poderá restabelecer o recurso de desvio para um único aplicativo se ele tiver sido desabilitado pela chave do Registro.  
  
 Quando você substitui o recurso de desvio, o nome forte é validado somente para correção, ele não é verificado para um <xref:System.Security.Permissions.StrongNameIdentityPermission>. Se você quiser confirmar um nome forte específico, precisará executar essa verificação separadamente.  
  
> [!IMPORTANT]
> A capacidade de forçar a validação de nome forte depende de uma chave do Registro, conforme descrito no procedimento a seguir. Se um aplicativo estiver em execução em uma conta que não tem permissão da ACL (lista de controle de acesso) para acessar essa chave do Registro, a configuração é ineficaz. Você deve garantir que os direitos da ACL estejam configurados para essa chave para que ela possa ser lida por todos os assemblies.  
  
## <a name="disable-the-strong-name-bypass-feature-for-all-applications"></a>Desabilitar o recurso de bypass de nome forte para todos os aplicativos  
  
- Em computadores de 32 bits, no Registro do sistema, crie uma entrada DWORD com um valor de 0 chamada `AllowStrongNameBypass` sob a chave HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework.  
  
- Em computadores de 64 bits, no Registro do sistema, crie uma entrada DWORD com um valor de 0 chamada `AllowStrongNameBypass` sob as chaves HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework e HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework.  
  
## <a name="disable-the-strong-name-bypass-feature-for-a-single-application"></a>Desabilitar o recurso de bypass de nome forte para um único aplicativo  
  
1. Abra ou crie o arquivo de configuração de aplicativo.  
  
    Para obter mais informações sobre esse arquivo, consulte a seção arquivos de configuração de aplicativo em [configurar aplicativos](../../framework/configure-apps/index.md).  
  
2. Adicione a seguinte entrada:  
  
    ```xml  
    <configuration>  
      <runtime>  
        <bypassTrustedAppStrongNames enabled="false" />  
      </runtime>  
    </configuration>  
    ```  
  
 Você pode restaurar o recurso de bypass para o aplicativo removendo a configuração do arquivo de configuração ou definindo o atributo como `true`.  
  
> [!NOTE]
> Você poderá ligar e desligar a validação de nome forte para um aplicativo somente se o recurso de desvio estiver habilitado para o computador. Se o recurso de desvio foi desativado para o computador, os nomes fortes são validados para todos os aplicativos e você não pode ignorar a validação para um único aplicativo.  
  
## <a name="see-also"></a>Consulte também

- [Sn.exe (Ferramenta Nome Forte)](../../framework/tools/sn-exe-strong-name-tool.md)
- [\<elemento de > bypassTrustedAppStrongNames](../../framework/configure-apps/file-schema/runtime/bypasstrustedappstrongnames-element.md)
- [Criar e usar assemblies de nome forte](create-use-strong-named.md)
