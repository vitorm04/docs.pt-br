---
title: "Segurança e Registro (Visual Basic)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- security [Visual Basic], registry
- registry, security issues
ms.assetid: 9980aff7-2f69-492b-8f66-29a9a76d3df5
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 2ca25e9ce82baf9d9f59ecd887aaf2cbb301f4e3
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="security-and-the-registry-visual-basic"></a>Segurança e Registro (Visual Basic)
Esta página discute as implicações de segurança de armazenar dados no Registro.  
  
## <a name="permissions"></a>Permissões  
 Não é seguro armazenar segredos, como senhas, no Registro como texto sem formatação, mesmo se a chave do Registro estiver protegida por ACLs (listas de controle de acesso).  
  
 Trabalhar com o Registro pode comprometer a segurança ao permitir o acesso inadequado aos recursos do sistema ou a informações protegidas. Para usar essas propriedades, é necessário ter lido e gravado permissões da enumeração <xref:System.Security.Permissions.RegistryPermissionAccess>, que controla o acesso a variáveis do Registro. Qualquer código sendo executado com confiança total (nos termos da política de segurança padrão, é qualquer código instalado no disco rígido local do usuário) tem as permissões necessárias para acessar o Registro. Para saber mais, confira a classe <xref:System.Security.Permissions.RegistryPermission>.  
  
 As variáveis de Registro não devem ser armazenadas em locais de memória em que o código sem <xref:System.Security.Permissions.RegistryPermission> possa acessá-los. Da mesma forma, ao conceder permissões, conceda os privilégios mínimos necessários para realizar o trabalho.  
  
 Os valores de acesso de permissão ao Registro são definidos pela enumeração <xref:System.Security.Permissions.RegistryPermissionAccess>. A tabela a seguir detalha seus membros.  
  
|Valor|Acesso às variáveis de Registro|  
|-----------|----------------------------------|  
|`AllAccess`|Criar, ler e gravar|  
|`Create`|Create|  
|`NoAccess`|Sem acesso|  
|`Read`|Ler|  
|`Write`|Write|  
  
## <a name="checking-values-in-registry-keys"></a>Verificando valores nas chaves do Registro  
 Ao criar um valor de Registro, é necessário decidir o que fazer se esse valor já existir. Outro processo, talvez um mal-intencionado, pode já ter criado o valor e tem acesso a ele. Ao colocar dados no valor de Registro, os dados estarão disponíveis para o outro processo. Para impedir isso, use o método `GetValue`. Ele retornará `Nothing` se a chave ainda não existir.  
  
> [!IMPORTANT]
>  Ao ler o Registro em um aplicativo Web, a identidade do usuário atual depende da autenticação e da representação implementadas no aplicativo Web.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>   
 [Lendo e Gravando do Registro](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)

