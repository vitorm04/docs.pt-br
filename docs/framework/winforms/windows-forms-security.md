---
title: "Segurança do Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- designer access security [Windows Forms]
- permissions [Windows Forms], Windows Forms
- Windows Forms, security
- security [Windows Forms]
- access control [Windows Forms], Windows Forms
- security policy [Windows Forms], Windows Forms
ms.assetid: 932d438a-5285-46d8-a958-8c93d0ad6cae
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8bd9b87fdfa54a6f9bf53e4fa897106257b4c625
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="windows-forms-security"></a>Segurança do Windows Forms
O Windows Forms oferece um modelo de segurança baseado em código (os níveis de segurança são definidos para o código, independentemente do usuário que o executa). Isso vai além de qualquer esquema de segurança que já pode estar em vigor no seu sistema de computador. Eles podem incluir os do navegador (como a segurança baseada em zonas disponível no Internet Explorer) ou do sistema operacional (como a segurança baseada em credenciais do Windows NT).  
  
## <a name="in-this-section"></a>Nesta seção  
 [Visão geral da segurança dos Windows Forms](../../../docs/framework/winforms/security-in-windows-forms-overview.md)  
 Explica brevemente o modelo de segurança do .NET Framework e as etapas básicas necessárias para garantir que o Windows Forms no seu aplicativo esteja seguro.  
  
 [Acesso mais seguro a arquivos e a dados nos Windows Forms](../../../docs/framework/winforms/more-secure-file-and-data-access-in-windows-forms.md)  
 Descreve como acessar arquivos e dados em um ambiente de confiança parcial.  
  
 [Impressão mais segura nos Windows Forms](../../../docs/framework/winforms/more-secure-printing-in-windows-forms.md)  
 Descreve como acessar recursos de impressão em um ambiente de confiança parcial.  
  
 [Considerações adicionais sobre segurança nos Windows Forms](../../../docs/framework/winforms/additional-security-considerations-in-windows-forms.md)  
 Descreve como realizar manipulação de janela, como usar a Área de Transferência e como fazer chamadas a código não gerenciado em um ambiente de confiança parcial.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [NIB: política de segurança padrão](http://msdn.microsoft.com/library/2c086873-0894-4f4d-8f7e-47427c1a3b55)  
 Lista as permissões padrão concedidas nos conjuntos de permissão de Confiança Total, Intranet Local e Internet.  
  
 [NIB: administração de política de segurança geral](http://msdn.microsoft.com/library/5121fe35-f0e3-402c-94ab-4f35b0a87b4b)  
 Fornece informações sobre como administrar a política de segurança do .NET Framework e elevar as permissões.  
  
 [Permissões perigosas e administração de política](../../../docs/framework/misc/dangerous-permissions-and-policy-administration.md)  
 Discute algumas permissões do .NET Framework que podem potencialmente permitir que o sistema de segurança seja contornado.  
  
 [Diretrizes de codificação segura](../../../docs/standard/security/secure-coding-guidelines.md)  
 Fornece links para tópicos que explicam as práticas recomendadas para escrever código com segurança no .NET Framework.  
  
 [NIB: solicitando permissões](http://msdn.microsoft.com/library/0447c49d-8cba-45e4-862c-ff0b59bebdc2)  
 Discute o uso de atributos que permitem que o tempo de execução saiba quais permissões seu código precisa executar.  
  
 [Principais conceitos de segurança](../../../docs/standard/security/key-security-concepts.md)  
 Links para tópicos que abrangem aspectos básicos de segurança de código.  
  
 [Noções Básicas da Segurança de Acesso do Código](../../../docs/framework/misc/code-access-security-basics.md)  
 Discute as noções básicas de trabalhar com a política de segurança de tempo de execução do .NET Framework.  
  
 [NIB: determinando quando modificar a política de segurança](http://msdn.microsoft.com/library/af749b17-e461-409d-84b9-a3d44789db16)  
 Explica como determinar quando seus aplicativos precisam divergir da política de segurança padrão.  
  
 [NIB: implantando a política de segurança](http://msdn.microsoft.com/library/f936c1e5-033b-4bd9-a3bd-a39ba733a681)  
 Discute a melhor maneira de implantar alterações de política de segurança.
