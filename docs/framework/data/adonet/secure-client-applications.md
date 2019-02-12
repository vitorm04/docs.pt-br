---
title: Proteger aplicativos cliente
ms.date: 03/30/2017
ms.assetid: 6239592e-fa7d-4dea-9f00-d296d0048b01
ms.openlocfilehash: c8efdf4c4baceb22ee60bdcf333ad1fec9ebd2d0
ms.sourcegitcommit: d2ccb199ae6bc5787b4762e9ea6d3f6fe88677af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56092703"
---
# <a name="secure-client-applications"></a>Proteger aplicativos cliente
Aplicativos geralmente consistem em várias partes que precisam ser protegidos contra vulnerabilidades que poderiam resultar em perda de dados ou comprometer o sistema. Criar interfaces do usuário segura pode impedir que muitos problemas, bloqueando os invasores antes que possam acessar dados ou recursos do sistema.  
  
## <a name="validate-user-input"></a>Validar a entrada do usuário  
 Ao construir um aplicativo que acessa os dados, você deve assumir que todas as entradas do usuário são mal-intencionada até que se prove o contrário. Falha ao fazer isso pode deixar seu aplicativo vulnerável a ataques. O .NET Framework contém classes para ajudá-lo a impor a um domínio de valores para os controles de entrada, como limitar o número de caracteres que podem ser inseridos. Ganchos de eventos permitem que você escreva procedimentos para verificar a validade dos valores. Dados de entrada do usuário podem ser validados e com rigidez de tipos, limitando a exposição do aplicativo para o script e injeção de SQL explora.  
  
> [!IMPORTANT]
>  Você também deve validar a entrada do usuário na fonte de dados, bem como no aplicativo cliente. Um invasor pode optar por ignorar seu aplicativo e atacar a fonte de dados diretamente.  
  
 [Segurança e entrada do usuário](../../../../docs/standard/security/security-and-user-input.md)  
 Descreve como lidar com bugs sutis e potencialmente perigosos que envolvem a entrada do usuário.  
  
 [Validação de entrada do usuário em páginas da Web do ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/7kh55542(v=vs.100))  
 Visão geral da validação de entrada do usuário usando controles de validação ASP.NET.  
  
 [Entrada do usuário nos Windows Forms](../../../../docs/framework/winforms/user-input-in-windows-forms.md)  
 Fornece links e informações de validação de mouse e teclado de entrada em um aplicativo Windows Forms.  
  
 [Expressões regulares do .NET Framework](../../../../docs/standard/base-types/regular-expressions.md)  
 Descreve como usar o <xref:System.Text.RegularExpressions.Regex> classe para verificar a validade da entrada do usuário.  
  
## <a name="windows-applications"></a>Aplicativos do Windows  
 No passado, os aplicativos de Windows geralmente são executados com permissões totais. O .NET Framework fornece a infraestrutura para restringir o código em execução em um aplicativo do Windows usando a segurança de acesso do código (CAS). No entanto, CAS sozinho não é suficiente para proteger seu aplicativo.  
  
 [Segurança do Windows Forms](../../../../docs/framework/winforms/windows-forms-security.md)  
 Discute como proteger aplicativos de formulários do Windows e fornece links para tópicos relacionados.  
  
 [Windows Forms e Aplicativos Não Gerenciados](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications.md)  
 Descreve como interagir com aplicativos não gerenciados em um aplicativo Windows Forms.  
  
 [Implantação do ClickOnce para Windows Forms](../../winforms/clickonce-deployment-for-windows-forms.md)  
 Descreve como usar `ClickOnce` implantação em um aplicativo Windows Forms e discute as implicações de segurança.  
  
## <a name="aspnet-and-xml-web-services"></a>ASP.NET e XML Web Services  
 Aplicativos ASP.NET geralmente precisam restringir o acesso a algumas partes do site da Web e fornecer outros mecanismos de proteção de dados e segurança do site. Estes links fornecem informações úteis para proteger seu aplicativo ASP.NET.  
  
 Um serviço Web XML fornece os dados que podem ser consumidos por um aplicativo ASP.NET, um aplicativo do Windows Forms ou outro serviço Web. Você precisa gerenciar a segurança para o serviço Web em si, bem como a segurança para o aplicativo cliente.  
  
 Para obter mais informações, consulte os seguintes recursos.  
  
|Recurso|Descrição|  
|--------------|-----------------|  
|[Protegendo Sites da Web do ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/91f66yxt(v=vs.100))|Discute como proteger aplicativos ASP.NET.|  
|[Protegendo serviços Web XML criados usando ASP.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w67h0dw7(v=vs.100))|Discute como implementar a segurança para um serviço Web ASP.NET.|  
|[Visão geral de explorações de script](https://docs.microsoft.com/previous-versions/aspnet/w1sw53ds(v=vs.100))|Discute como se proteger contra um ataque de exploração de script, que tenta inserir caracteres mal-intencionado em uma página da Web.|  
|[Práticas recomendadas de segurança básica para aplicativos Web](https://docs.microsoft.com/previous-versions/aspnet/zdh19h94(v=vs.100))|Informações gerais sobre segurança e links para obter mais detalhes,|  
  
## <a name="remoting"></a>Comunicação Remota  
 Comunicação remota do .NET permite que você crie aplicativos amplamente distribuídos com facilidade, se os componentes do aplicativo estão todos em um computador ou distribuídos em todo o mundo inteiro. Você pode criar aplicativos cliente que usam objetos em outros processos no mesmo computador ou em qualquer outro computador que pode ser acessado pela sua rede. Você também pode usar a comunicação remota do .NET para se comunicar com outros domínios de aplicativo no mesmo processo.  
  
|Recurso|Descrição|  
|--------------|-----------------|  
|[Configuração de aplicativos remotos](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/b8tysty8(v=vs.100))|Discute como configurar aplicativos de comunicação remota para evitar problemas comuns.|  
|[Segurança na comunicação remota](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/9hwst9th(v=vs.100))|Descreve a autenticação e criptografia, bem como tópicos de segurança adicionais relevantes para a comunicação remota.|  
|[Segurança e considerações de comunicação remota](../../../../docs/framework/misc/security-and-remoting-considerations.md)|Descreve problemas de segurança com objetos protegidos e o cruzamento de domínio de aplicativo.|  
  
## <a name="see-also"></a>Consulte também
- [Securing ADO.NET Applications](../../../../docs/framework/data/adonet/securing-ado-net-applications.md) (Protegendo aplicativos ADO.NET)
- [Recomendações para estratégias de acesso a dados](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/8fxztkff(v=vs.90))
- [Protegendo aplicativos](/visualstudio/ide/securing-applications)
- [Protegendo informações de conexão](../../../../docs/framework/data/adonet/protecting-connection-information.md)
- [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
