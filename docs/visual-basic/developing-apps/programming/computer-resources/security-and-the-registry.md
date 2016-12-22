---
title: "Seguran&#231;a e Registro (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "registro, problemas de segurança"
  - "segurança [Visual Basic], registro"
ms.assetid: 9980aff7-2f69-492b-8f66-29a9a76d3df5
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Seguran&#231;a e Registro (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Esta página descreve as implicações de segurança do armazenamento de dados no Registro.  
  
## Permissões  
 Não é seguro armazenar segredos, como senhas, no Registro como texto sem\-formatação, mesmo se a chave do Registro estiver protegida por ACLs \(listas de controle de acesso\).  
  
 Trabalhar com o Registro pode comprometer a segurança, permitindo inadequado acesso aos recursos do sistema ou a informações protegidas.  Para usar essas propriedades, você deve ter permissões para leitura e escrita de enumeração <xref:System.Security.Permissions.RegistryPermissionAccess> , que controla o acesso a variáveis do Registro.  Qualquer código sendo executado com confiança total \(sob o política de segurança padrão, este é qualquer código instalado no disco rígido local do usuário\) tem as permissões necessárias para acessar o Registro.  Para mais informações, consulte a classe <xref:System.Security.Permissions.RegistryPermission>.  
  
 Variáveis de registro não devem ser armazenadas em locais de memória onde o código sem <xref:System.Security.Permissions.RegistryPermission> possa acessá\-los.  Da mesma forma, quando conceder as permissões, conceda os privilégios mínimos necessários para obter o trabalho feito.  
  
 Valores de acesso a permissões do registro são definidos pela enumeração <xref:System.Security.Permissions.RegistryPermissionAccess>.  A tabela a seguir detalha seus membros.  
  
|Valor|Acesso a variáveis de registro.|  
|-----------|-------------------------------------|  
|`AllAccess`|Criar, Ler e Gravar|  
|`Create`|Create|  
|`NoAccess`|Sem acesso.|  
|`Read`|Read|  
|`Write`|Write|  
  
## Verificar valores em chaves do Registro  
 Quando você cria um valor do registro, é preciso decidir o que fazer se esse valor já existe.  Outro processo, talvez um arquivo mal\-intencionado, talvez já criou o valor e faz acesso a ele.  Quando você coloca o valor dos dados no valor do registro, os dados estão disponíveis para o outro processo.  Para evitar isso, use o método `GetValue`.  Ele retorna `Nothing` se a chave ainda não existir.  
  
> [!IMPORTANT]
>  Quando se está lendo o registro a partir de um aplicativo da Web, a identidade do usuário atual depende da autenticação e representação implementada no aplicativo Web.  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>   
 [Lendo e gravando a partir do Registro](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)