---
title: "Como excluir uma chave do Registro no Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.DeleteSetting"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "exemplos [Visual Basic], registro"
  - "Função GetAllSettings"
  - "Função GetSetting"
  - "chaves do registro, excluindo"
  - "registro, excluindo teclas"
  - "registro, excluindo valores"
ms.assetid: ab9aca0e-42b0-4ff7-8ff9-845a4bfdf9f2
caps.latest.revision: 28
caps.handback.revision: 28
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como excluir uma chave do Registro no Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Os métodos <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%29> e <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%2CSystem.Boolean%29> podem ser usados para excluir chaves do Registro.  
  
## Procedimento  
  
#### Para excluir uma chave do Registro  
  
-   Use o método  `DeleteSubKey` para excluir uma chave do Registro.  Este exemplo exclui a chave Software\/TestApp na ramificação \(hive\) CurrentUser.  Você pode alterar isso no código para a cadeia de caracteres apropriada, ou ainda deixar com que ela dependa de informações fornecidas pelo usuário.  
  
     [!code-vb[VbResourceTasks#19](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-delete-a-registry-key_1.vb)]  
  
## Programação robusta  
 O método `DeleteSubKey` retorna uma cadeia de caracteres vazia se o par chave\/valor não existir.  
  
 As seguintes condições podem causar uma exceção:  
  
-   O nome da chave é `Nothing` \(<xref:System.ArgumentNullException>\).  
  
-   O usuário não tem permissões para apagar chaves do Registro \(<xref:System.Security.SecurityException>\).  
  
-   O nome da chave excede o limite de 255 caracteres \(<xref:System.ArgumentException>\).  
  
-   A chave do Registro é somente leitura \(<xref:System.UnauthorizedAccessException>\).  
  
## Segurança do .NET Framework  
 Chamadas ao Registro falham tanto se não tiverem permissões de tempo de execução suficientes \(<xref:System.Security.Permissions.RegistryPermission>\) quanto se o usuário não tiver o acesso correto \(conforme determinado pelas ACLs\) para criar ou gravar nas configurações.  Por exemplo, um aplicativo local que possui a permissão de segurança de acesso ao código talvez não tenha permissão de sistema operacional.  
  
## Consulte também  
 <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%2A>   
 <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%2A>   
 <xref:Microsoft.Win32.RegistryKey>   
 [Segurança e Registro](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md)   
 [Lendo e gravando a partir do Registro](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)