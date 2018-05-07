---
title: Proteger aplicativos cliente
ms.date: 03/30/2017
ms.assetid: 6239592e-fa7d-4dea-9f00-d296d0048b01
ms.openlocfilehash: ac4f1c3debacd89a0763aa8f30de3c5463c5d24d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="secure-client-applications"></a>Proteger aplicativos cliente
Aplicativos normalmente consistem em muitas partes que precisam ser protegidos contra vulnerabilidades que podem resultar na perda de dados ou comprometer o sistema. Criando interfaces de usuário segura pode impedir que muitos problemas bloqueando os invasores antes que possam acessar dados ou recursos do sistema.  
  
## <a name="validate-user-input"></a>Validar a entrada do usuário  
 Ao construir um aplicativo que acessa os dados, você deve presumir que todas as entradas do usuário são mal-intencionada até que se prove o contrário. Falha ao fazer isso pode deixar seu aplicativo vulnerável a ataques. O .NET Framework contém classes para ajudar a impor um domínio de valores para controles de entrada, como limitar o número de caracteres que podem ser inseridos. Ganchos de eventos permitem que você grave procedimentos para verificar a validade dos valores. Dados de entrada de usuário podem ser validados e fortemente tipada, limitando a exposição do aplicativo para script e injeção de SQL explora.  
  
> [!IMPORTANT]
>  Você também deve validar a entrada do usuário na fonte de dados, bem como o aplicativo cliente. Um invasor pode optar por ignorar seu aplicativo e ataques a fonte de dados diretamente.  
  
 [Segurança e entrada do usuário](../../../../docs/standard/security/security-and-user-input.md)  
 Descreve como manipular erros sutis e potencialmente perigosos que envolvem a entrada do usuário.  
  
 [Validando a entrada do usuário em páginas da Web do ASP.NET](http://msdn.microsoft.com/library/4ad3dacb-89e0-4cee-89ac-40a3f2a85461)  
 Visão geral de validação de entrada do usuário usando controles de validação ASP.NET.  
  
 [Entrada do usuário nos Windows Forms](../../../../docs/framework/winforms/user-input-in-windows-forms.md)  
 Fornece links e informações de validação de entrada em um aplicativo do Windows Forms de teclado e mouse.  
  
 [Expressões regulares do .NET Framework](../../../../docs/standard/base-types/regular-expressions.md)  
 Descreve como usar o <xref:System.Text.RegularExpressions.Regex> classe para verificar a validade da entrada do usuário.  
  
## <a name="windows-applications"></a>Aplicativos do Windows  
 No passado, aplicativos do Windows geralmente é executado com permissões totais. O .NET Framework fornece a infraestrutura para restringir o código em execução em um aplicativo do Windows usando a segurança de acesso ao código (CAS). No entanto, CAS sozinho não é suficiente para proteger seu aplicativo.  
  
 [Segurança do Windows Forms](../../../../docs/framework/winforms/windows-forms-security.md)  
 Descreve como proteger os aplicativos de formulários do Windows e fornece links para tópicos relacionados.  
  
 [Windows Forms e Aplicativos Não Gerenciados](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications.md)  
 Descreve como interagir com aplicativos não gerenciados em um aplicativo do Windows Forms.  
  
 [Aplicativos de implantação de ClickOnce para Windows Forms](http://msdn.microsoft.com/library/34d8c770-48f2-460c-8d67-4ea5684511df)  
 Descreve como usar `ClickOnce` implantação em um aplicativo do Windows Forms e discute as implicações de segurança.  
  
## <a name="aspnet-and-xml-web-services"></a>ASP.NET e serviços Web XML  
 Aplicativos ASP.NET em geral é necessário restringir o acesso a algumas partes do site e fornecer outros mecanismos para proteção de dados e segurança do site. Estes links fornecem informações úteis para proteger seu aplicativo ASP.NET.  
  
 Um serviço Web XML fornece os dados que podem ser consumidos por um aplicativo ASP.NET, um aplicativo Windows Forms ou outro serviço Web. Você precisa gerenciar segurança do serviço da Web em si, bem como a segurança para o aplicativo cliente.  
  
 Para obter mais informações, consulte os seguintes recursos.  
  
|Recurso|Descrição|  
|--------------|-----------------|  
|[NIB: Segurança do ASP.NET](http://msdn.microsoft.com/library/04b37532-18d9-40b4-8e5f-ee09a70b311d)|Descreve como proteger aplicativos ASP.NET.|  
|[Protegendo XML Web Services criado usando ASP.NET](http://msdn.microsoft.com/library/354b2ab1-2782-4542-b32a-dc560178b90c)|Descreve como implementar a segurança para um serviço Web ASP.NET.|  
|[Visão geral de explorações de script](http://msdn.microsoft.com/library/772c7312-211a-4eb3-8d6e-eec0aa1dcc07)|Descreve como proteger contra um ataque de exploração de script, que tenta inserir caracteres mal-intencionado em uma página da Web.|  
|[NIB: Basic práticas de segurança para aplicativos Web ASP.NET](http://msdn.microsoft.com/library/94a52ab8-731d-417e-b997-721baf43df38)|Informações gerais sobre segurança e links para aprofundar,|  
  
## <a name="remoting"></a>Comunicação Remota  
 Comunicação remota do .NET permite que você crie aplicativos amplamente distribuídos com facilidade, se os componentes do aplicativo estão todos em um computador ou distribuídos em todo o mundo inteiro. Você pode criar aplicativos cliente que usam objetos em outros processos no mesmo computador ou em qualquer outro computador que pode ser acessado pela rede. Você também pode usar a comunicação remota do .NET para se comunicar com outros domínios de aplicativo no mesmo processo.  
  
|Recurso|Descrição|  
|--------------|-----------------|  
|[Configuração de aplicativos remotos](http://msdn.microsoft.com/library/92c0c097-d984-4315-835b-7490ecdf1097)|Discute como configurar aplicativos remotos para evitar problemas comuns.|  
|[Segurança de comunicação remota](http://msdn.microsoft.com/library/9574262c-d4b1-41c5-8600-24ff147c0add)|Descreve a autenticação e criptografia, bem como os tópicos adicionais de segurança relevantes para comunicação remota.|  
|[Segurança e considerações de comunicação remota](../../../../docs/framework/misc/security-and-remoting-considerations.md)|Descreve problemas de segurança com objetos protegidos e a interseção do domínio de aplicativo.|  
  
## <a name="see-also"></a>Consulte também  
 [Securing ADO.NET Applications](../../../../docs/framework/data/adonet/securing-ado-net-applications.md) (Protegendo aplicativos ADO.NET)  
 [Recomendações para estratégias de acesso de dados](http://msdn.microsoft.com/library/72411f32-d12a-4de8-b961-e54fca7faaf5)  
 [Protegendo aplicativos](/visualstudio/ide/securing-applications)  
 [Protegendo informações de conexão](../../../../docs/framework/data/adonet/protecting-connection-information.md)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
