---
title: Como desabilitar a funcionalidade de desvio de nome forte
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- strong-name bypass feature
- strong-named assemblies, loading into trusted application domains
ms.assetid: 234e088c-3b11-495a-8817-e0962be79d82
caps.latest.revision: 30
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 0af565c6d27be6a5a22bfb0fd1f90e4e46deec33
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-disable-the-strong-name-bypass-feature"></a>Como desabilitar a funcionalidade de desvio de nome forte
Desde o .NET Framework versão 3.5 Service Pack 1 (SP1), as assinaturas de nome forte não são validadas quando um assembly é carregado em um objeto <xref:System.AppDomain> de confiança total, como o <xref:System.AppDomain> padrão para a zona `MyComputer`. Isso é conhecido como o recurso de desvio de nome forte. Em um ambiente de confiança total, as exigências de <xref:System.Security.Permissions.StrongNameIdentityPermission> sempre têm êxito para assemblies assinados de confiança total, independentemente de sua assinatura. A única restrição é que o assembly deve ser totalmente confiável porque sua zona é totalmente confiável. Como o nome forte não é um fator determinante sob essas condições, não há nenhum motivo para ser validado. Ignorar a validação de assinaturas de nome forte fornece melhorias significativas de desempenho.  
  
 O recurso de desvio se aplica a qualquer assembly de confiança total que não é assinado com atraso e que é carregado em qualquer <xref:System.AppDomain> de confiança total no diretório especificado por sua propriedade <xref:System.AppDomainSetup.ApplicationBase%2A>.  
  
 Você pode substituir o recurso de desvio para todos os aplicativos em um computador definindo um valor de chave do Registro. Você pode substituir a configuração de um único aplicativo usando um arquivo de configuração de aplicativo. Você não poderá restabelecer o recurso de desvio para um único aplicativo se ele tiver sido desabilitado pela chave do Registro.  
  
 Quando você substitui o recurso de desvio, o nome forte é validado somente para correção, ele não é verificado para um <xref:System.Security.Permissions.StrongNameIdentityPermission>. Se você quiser confirmar um nome forte específico, precisará executar essa verificação separadamente.  
  
> [!IMPORTANT]
>  A capacidade de forçar a validação de nome forte depende de uma chave do Registro, conforme descrito no procedimento a seguir. Se um aplicativo estiver em execução em uma conta que não tem permissão da ACL (lista de controle de acesso) para acessar essa chave do Registro, a configuração é ineficaz. Você deve garantir que os direitos da ACL estejam configurados para essa chave para que ela possa ser lida por todos os assemblies.  
  
### <a name="to-disable-the-strong-name-bypass-feature-for-all-applications"></a>Para desabilitar o recurso de desvio de nome forte para todos os aplicativos  
  
-   Em computadores de 32 bits, no Registro do sistema, crie uma entrada DWORD com um valor de 0 chamada `AllowStrongNameBypass` sob a chave HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework.  
  
-   Em computadores de 64 bits, no Registro do sistema, crie uma entrada DWORD com um valor de 0 chamada `AllowStrongNameBypass` sob as chaves HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework e HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework.  
  
### <a name="to-disable-the-strong-name-bypass-feature-for-a-single-application"></a>Para desabilitar o recurso de desvio de nome forte para um único aplicativo  
  
1.  Abra ou crie o arquivo de configuração de aplicativo.  
  
     Para obter mais informações sobre esse arquivo, consulte a seção Application Configuration Files (Arquivos de configuração de aplicativo) em [Configuring Apps](../../../docs/framework/configure-apps/index.md) (Configurando aplicativos).  
  
2.  Adicione a seguinte entrada:  
  
    ```xml  
    <configuration>  
      <runtime>  
        <bypassTrustedAppStrongNames enabled="false" />  
      </runtime>  
    </configuration>  
    ```  
  
 Você pode restaurar o recurso de desvio para o aplicativo removendo a definição do arquivo de configuração ou definindo o atributo como “true”.  
  
> [!NOTE]
>  Você poderá ligar e desligar a validação de nome forte para um aplicativo somente se o recurso de desvio estiver habilitado para o computador. Se o recurso de desvio foi desativado para o computador, os nomes fortes são validados para todos os aplicativos e você não pode ignorar a validação para um único aplicativo.  
  
## <a name="see-also"></a>Consulte também  
 [Sn.exe (Ferramenta Nome Forte)](../../../docs/framework/tools/sn-exe-strong-name-tool.md)   
 [Elemento \<bypassTrustedAppStrongNames>](../../../docs/framework/configure-apps/file-schema/runtime/bypasstrustedappstrongnames-element.md)   
 [Criando e usando assemblies com nome forte](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)

