---
title: "Como criar uma chave do Registro e definir o valor no Visual Basic: | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "RegistryKey.CreateSubKey"
  - "RegistryKey.SetValue"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "exemplos [Visual Basic], registro"
  - "chaves do registro, criando"
  - "chaves do registro, configurando valores"
  - "registro, adicionando chaves"
  - "registro, adicionando valores"
ms.assetid: d3e40f74-c283-480c-ab18-e5e9052cd814
caps.latest.revision: 30
caps.handback.revision: 30
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como criar uma chave do Registro e definir o valor no Visual Basic:
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

O método `CreateSubKey` do objeto `My.Computer.Registry` pode ser usado para criar uma chave do Registro.  
  
## Procedimento  
  
#### Para criar uma chave do Registro  
  
-   Use o método `CreateSubKey`, especificando em que seção colocar a chave, bem como o nome da chave.  O parâmetro  `Subkey`  é não diferencia maiúsculas de minúsculas.  Este exemplo cria a chave de registro `MyTestKey` em HKEY\_CURRENT\_USER.  
  
     [!code-vb[VbResourceTasks#17](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-create-a-registry-key-and-set-its-value_1.vb)]  
  
#### Para criar uma chave do Registro e definir um valor dentro dela  
  
1.  Use o método `CreateSubkey`, especificando em que seção colocar a chave, bem como o nome da chave.  Este exemplo cria a chave de registro `MyTestKey` em HKEY\_CURRENT\_USER.  
  
     [!code-vb[VbResourceTasks#17](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-create-a-registry-key-and-set-its-value_1.vb)]  
  
2.  Defina o valor com o método `SetValue`.  Este exemplo define a valor da cadeia de caracteres. "  MyTestKeyValue"para"Este é um valor de teste".  
  
     [!code-vb[VbResourceTasks#14](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-create-a-registry-key-and-set-its-value_2.vb)]  
  
## Exemplo  
 Este exemplo cria o chave do Registro `MyTestKey` em HKEY\_CURRENT\_USER e, em seguida, define o valor da cadeia de caracteres `MyTestKeyValue` para `This is a test value`.  
  
 [!code-vb[VbResourceTasks#15](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-create-a-registry-key-and-set-its-value_3.vb)]  
  
## Programação robusta  
 Examine a estrutura do Registro para localizar um local adequado para a sua chave.  Por exemplo, você pode desejar abrir a chave HKEY\_CURRENT\_USER\\\\Software do usuário atual, e criar uma chave com nome da sua empresa.  Em seguida, adicione os valores do registro a chave da sua empresa.  
  
 Quando se esta lendo o registro para um aplicativo da Web, o usuário atual depende da autenticação e representação implementada no aplicativo da Web.  
  
 É mais seguro gravar dados na pasta de usuário \(<xref:Microsoft.Win32.Registry.CurrentUser>\) em vez de no computador local \(<xref:Microsoft.Win32.Registry.LocalMachine>\).  
  
 Quando você cria um valor do registro, é preciso decidir o que fazer se esse valor já existe.  Outro processo, talvez um arquivo mal\-intencionado, talvez já criou o valor e faz acesso a ele.  Quando você coloca o valor dos dados no valor do registro, os dados estão disponíveis para o outro processo.  Para evitar isso, use o método <xref:Microsoft.Win32.RegistryKey.GetValue%2A>.  Ele retorna `Nothing` se a chave ainda não existir.  
  
 Ele é não seguro para armazenamento de segredos, como senhas, ele registra como texto simples, mesmo se a chave do registro estiver protegido por ACLs\) \(listas de controle de acesso.  
  
 As seguintes condições podem causar uma exceção:  
  
-   O nome da chave é `Nothing` \(<xref:System.ArgumentNullException>\).  
  
-   O usuário não tem permissões para criar chaves do Registro \(<xref:System.Security.SecurityException>\).  
  
-   O nome da chave excede o limite de 255 caracteres \(<xref:System.ArgumentException>\).  
  
-   A chave é fechada \(<xref:System.IO.IOException>\).  
  
-   A chave do Registro é somente leitura \(<xref:System.UnauthorizedAccessException>\).  
  
## Segurança do .NET Framework  
 Para executar esse processo, seu assembly requer um nível de privilégio concedido pela classe <xref:System.Security.Permissions.RegistryPermission>.  Se você estiver executando em um contexto parcialmente confiável, o código pode lançar uma exceção devido a privilégios insuficientes.  Da mesma forma, o usuário deve ter as ACLs corretas para criar ou gravar as configurações.  Por exemplo, um aplicativo local que possui a permissão de segurança de acesso ao código talvez não tenha permissão de sistema operacional.  Para mais informações, consulte [Noções básicas da segurança de acesso do código](../Topic/Code%20Access%20Security%20Basics.md).  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>   
 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy.CurrentUser%2A>   
 <xref:Microsoft.Win32.RegistryKey.CreateSubKey%2A>   
 [Lendo e gravando a partir do Registro](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)   
 [Noções básicas da segurança de acesso do código](../Topic/Code%20Access%20Security%20Basics.md)