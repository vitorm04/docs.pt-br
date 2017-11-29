---
title: 'Como criar uma chave do Registro e definir o valor no Visual Basic:'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- RegistryKey.CreateSubKey
- RegistryKey.SetValue
helpviewer_keywords:
- registry keys [Visual Basic], creating
- registry [Visual Basic], adding values
- registry [Visual Basic], adding keys
- registry keys [Visual Basic], setting values
- examples [Visual Basic], registry
ms.assetid: d3e40f74-c283-480c-ab18-e5e9052cd814
caps.latest.revision: "30"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b6e71c106592490b92cf6f2dc02e59cddb28b95d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-registry-key-and-set-its-value-in-visual-basic"></a>Como criar uma chave do Registro e definir o valor no Visual Basic:
O método `CreateSubKey` do objeto `My.Computer.Registry` pode ser usado para criar uma chave do Registro.  
  
## <a name="procedure"></a>Procedimento  
  
#### <a name="to-create-a-registry-key"></a>Criar uma chave do Registro  
  
-   Use o método `CreateSubKey` especificando em qual hive a chave será colocada, bem como o nome da chave. O parâmetro `Subkey` não diferencia maiúsculas e minúsculas. Este exemplo cria a chave do Registro `MyTestKey` em HKEY_CURRENT_USER.  
  
     [!code-vb[VbResourceTasks#17](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-create-a-registry-key-and-set-its-value_1.vb)]  
  
#### <a name="to-create-a-registry-key-and-set-a-value-in-it"></a>Criar uma chave do Registro e definir o valor  
  
1.  Use o método `CreateSubkey` especificando em qual hive a chave será colocada, bem como o nome da chave. Este exemplo cria a chave do Registro `MyTestKey` em HKEY_CURRENT_USER.  
  
     [!code-vb[VbResourceTasks#17](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-create-a-registry-key-and-set-its-value_1.vb)]  
  
2.  Defina o valor com o método `SetValue`. Este exemplo define o valor da cadeia de caracteres. De "MyTestKeyValue" para "Este é um valor de teste".  
  
     [!code-vb[VbResourceTasks#14](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-create-a-registry-key-and-set-its-value_2.vb)]  
  
## <a name="example"></a>Exemplo  
 Este exemplo cria a chave do Registro `MyTestKey` em HKEY_CURRENT_USER e, em seguida, define o valor da cadeia de caracteres de `MyTestKeyValue` para `This is a test value`.  
  
 [!code-vb[VbResourceTasks#15](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-create-a-registry-key-and-set-its-value_3.vb)]  
  
## <a name="robust-programming"></a>Programação robusta  
 Analise a estrutura do Registro para encontrar um local adequado para a chave. Por exemplo, caso você queira abrir a chave HKEY_CURRENT_USER\Software do usuário atual e criar uma chave com o nome da empresa. Em seguida, adicione os valores do Registro à chave da empresa.  
  
 Ao ler o Registro de um aplicativo Web, o usuário atual depende da autenticação e da representação implementadas no aplicativo Web.  
  
 É mais seguro gravar dados na pasta do usuário (<xref:Microsoft.Win32.Registry.CurrentUser>) em vez de no computador local (<xref:Microsoft.Win32.Registry.LocalMachine>).  
  
 Ao criar um valor de Registro, é necessário decidir o que fazer se esse valor já existir. Outro processo, talvez um mal-intencionado, pode já ter criado o valor e tem acesso a ele. Ao colocar dados no valor de Registro, os dados estarão disponíveis para o outro processo. Para impedir isso, use o método <xref:Microsoft.Win32.RegistryKey.GetValue%2A>. Ele retornará `Nothing` se a chave ainda não existir.  
  
 Não é seguro armazenar segredos, como senhas, no Registro como texto sem formatação, mesmo se a chave do Registro estiver protegida por ACLs (Listas de Controle de Acesso).  
  
 As seguintes condições podem causar uma exceção:  
  
-   O nome da chave é `Nothing` (<xref:System.ArgumentNullException>).  
  
-   O usuário não tem permissões para criar chaves do Registro (<xref:System.Security.SecurityException>).  
  
-   O nome da chave excede o limite de 255 caracteres (<xref:System.ArgumentException>).  
  
-   A chave é fechada (<xref:System.IO.IOException>).  
  
-   A chave do Registro é somente leitura (<xref:System.UnauthorizedAccessException>).  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 Para executar esse processo, seu assembly exige um nível de privilégio concedido pela classe <xref:System.Security.Permissions.RegistryPermission>. Se você estiver executando em um contexto de confiança parcial, o processo poderá gerar uma exceção em razão dos privilégios insuficientes. Da mesma forma, o usuário deve ter as ACLs corretas para criar ou gravar nas configurações. Por exemplo, um aplicativo local que tem a permissão de segurança de acesso do código pode não ter permissão do sistema operacional. Para obter mais informações, consulte [Noções Básicas da Segurança de Acesso do Código](https://msdn.microsoft.com/library/33tceax8).  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>  
 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy.CurrentUser%2A>  
 <xref:Microsoft.Win32.RegistryKey.CreateSubKey%2A>  
 [Lendo e Gravando do Registro](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)  
 [Noções Básicas da Segurança de Acesso do Código](https://msdn.microsoft.com/library/33tceax8)
