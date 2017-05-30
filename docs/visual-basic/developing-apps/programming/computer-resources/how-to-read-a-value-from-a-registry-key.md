---
title: Como ler um valor de uma chave do Registro no Visual Basic | Microsoft Docs
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
- registry keys, determining if a value exists in
- My.Computer.Registry object, examples
- registry, determining if values exist
- registry keys, reading from
- registry, reading
ms.assetid: 775d0a57-68c9-464e-8949-9a39bd29cc64
caps.latest.revision: 31
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: b5054e277895d185ab8ec6f6a2950d5dedbef390
ms.contentlocale: pt-br
ms.lasthandoff: 05/22/2017

---
# <a name="how-to-read-a-value-from-a-registry-key-in-visual-basic"></a>Como ler um valor a partir de uma chave do Registro no Visual Basic
O método `GetValue` do objeto `My.Computer.Registry` pode ser usado para ler valores no Registro do Windows.  
  
 Se a chave, "Software\MyApp" no exemplo a seguir, não existir, uma exceção será gerada. Se o `ValueName`, "Name" no exemplo a seguir, não existir, `Nothing` será retornado.  
  
 O método `GetValue` também pode ser usado para determinar se um determinado valor existe em uma chave do Registro específica.  
  
 Quando o código lê o Registro de um aplicativo Web, o usuário atual será determinado pela autenticação e a representação implementadas no aplicativo Web.  
  
### <a name="to-read-a-value-from-a-registry-key"></a>Para ler um valor de uma chave do Registro  
  
-   Use o método `GetValue` (especificando o caminho e nome) para ler um valor de chave do Registro. O exemplo a seguir lê o valor `Name` de `HKEY_CURRENT_USER\Software\MyApp` e o exibe em uma caixa de mensagem.  
  
     [!code-vb[VbResourceTasks#4](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-read-a-value-from-a-registry-key_1.vb)]  
  
 Este exemplo de código também está disponível como um trecho de código do IntelliSense. No seletor de trecho de código, ele está localizado em **Sistema Operacional Windows > Registro**. Para obter mais informações, consulte [Trechos de Código](https://docs.microsoft.com/visualstudio/ide/code-snippets).  
  
### <a name="to-determine-whether-a-value-exists-in-a-registry-key"></a>Para determinar se um valor existe em uma chave do Registro  
  
-   Use o método `GetValue` para recuperar o valor. O código a seguir verifica se o valor existe e retorna uma mensagem se ele não existir.  
  
     [!code-vb[VbResourceTasks#12](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-read-a-value-from-a-registry-key_2.vb)]  
  
## <a name="robust-programming"></a>Programação robusta  
 O Registro contém chaves de nível superior ou raiz, que são usadas para armazenar dados. Por exemplo, a chave raiz HKEY_LOCAL_MACHINE é usada para armazenar configurações de nível do computador usadas por todos os usuários, enquanto HKEY_CURRENT_USER é usada para armazenar dados específicos a um usuário individual.  
  
 As seguintes condições podem causar uma exceção:  
  
-   O nome da chave é `Nothing` (<xref:System.ArgumentNullException>).  
  
-   O usuário não tem permissões para ler nas chaves do Registro (<xref:System.Security.SecurityException>).  
  
-   O nome da chave excede o limite de 255 caracteres (<xref:System.ArgumentException>).  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 Para executar esse processo, seu assembly exige um nível de privilégio concedido pela classe <xref:System.Security.Permissions.RegistryPermission>. Se você estiver executando em um contexto de confiança parcial, o processo poderá gerar uma exceção em razão dos privilégios insuficientes. Da mesma forma, o usuário deve ter as ACLs corretas para criar ou gravar nas configurações. Por exemplo, um aplicativo local que tem a permissão de segurança de acesso do código pode não ter permissão do sistema operacional. Para obter mais informações, consulte [Noções Básicas da Segurança de Acesso do Código](https://msdn.microsoft.com/library/33tceax8).  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>   
 <xref:Microsoft.Win32.RegistryHive>   
 [Lendo e Gravando do Registro](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
