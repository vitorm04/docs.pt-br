---
title: "Como ler um valor a partir de uma chave do Registro no Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "Objeto My.Computer.Registry, exemplos"
  - "chaves do registro, determinando se um valor existe em"
  - "chaves do registro, lendo de"
  - "registro, determinando se valores existem"
  - "registro, lendo"
ms.assetid: 775d0a57-68c9-464e-8949-9a39bd29cc64
caps.latest.revision: 31
caps.handback.revision: 31
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como ler um valor a partir de uma chave do Registro no Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

O método `GetValue` do objeto `My.Computer.Registry` pode ser usado para gravar valores no Registro do Windows.  
  
 Se não existir, a chave, "Software\\MyApp" no exemplo a seguir, uma exceção é lançada.  Se a `ValueName`, "Nome" no exemplo a seguir, não existe, `Nothing` é retornado.  
  
 O `GetValue` método também pode ser usado para determinar se um determinado valor existe em uma chave do Registro específica.  
  
 Quando o código lê o registro de um aplicativo da Web, o usuário atual é determinado da autenticação e representação implementada no aplicativo da Web.  
  
### Para ler um valor de uma Chave do Registro  
  
-   Use o método `GetValue`, especificando o caminho e o nome para ler um valor da chave do registro.  O exemplo a seguir lê o valor `Name` do `HKEY_CURRENT_USER\Software\MyApp` e o exibe em uma caixa de mensagem.  
  
     [!code-vb[VbResourceTasks#4](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-read-a-value-from-a-registry-key_1.vb)]  
  
 Este exemplo de código também está disponível como um trecho de código IntelliSense.  No selecionador de trechos de código, ele está localizado em **Windows Operating System \> Registry**.  Para mais informações, consulte [Trechos de código](/visual-studio/ide/code-snippets).  
  
### Para determinar se um valor existe em uma Chave do Registro  
  
-   Use o método `GetValue` para recuperar o valor.  O código a seguir verifica se o valor existir e retorna uma mensagem se não existir.  
  
     [!code-vb[VbResourceTasks#12](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-read-a-value-from-a-registry-key_2.vb)]  
  
## Programação robusta  
 O registro possui chaves de alto nível, ou raiz, que são usadas para armazenar dados.  Por exemplo, a chave raiz HKEY\_LOCAL\_MACHINE é usada para armazenar configurações a nível de máquina usadas por todos os usuários, enquanto HKEY\_CURRENT\_USER é usada para armazenar dados específicos para um usuário individual  
  
 As seguintes condições podem causar uma exceção:  
  
-   O nome da chave é `Nothing` \(<xref:System.ArgumentNullException>\).  
  
-   O usuário não tem permissões para ler das chaves do Registro \(<xref:System.Security.SecurityException>\).  
  
-   O nome da chave excede o limite de 255 caracteres \(<xref:System.ArgumentException>\).  
  
## Segurança do .NET Framework  
 Para executar esse processo, seu assembly requer um nível de privilégio concedido pela classe <xref:System.Security.Permissions.RegistryPermission>.  Se você estiver executando em um contexto parcialmente confiável, o código pode lançar uma exceção devido a privilégios insuficientes.  Da mesma forma, o usuário deve ter as ACLs corretas para criar ou gravar as configurações.  Por exemplo, um aplicativo local que possui a permissão de segurança de acesso ao código talvez não tenha permissão de sistema operacional.  Para mais informações, consulte [Noções básicas da segurança de acesso do código](../Topic/Code%20Access%20Security%20Basics.md).  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>   
 <xref:Microsoft.Win32.RegistryHive>   
 [Lendo e gravando a partir do Registro](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)