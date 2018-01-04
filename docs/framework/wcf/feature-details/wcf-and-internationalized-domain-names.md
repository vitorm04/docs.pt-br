---
title: "WCF e nomes de domínio internacionalizados"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c8a3e10a-8bc2-4a78-8d86-a562ba6e65fa
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7a0a6cd2a809648aadfba9bac2c4ab35c26b4c65
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="wcf-and-internationalized-domain-names"></a>WCF e nomes de domínio internacionalizados
Foi adicionado suporte para permitir que os serviços WCF com nomes de domínio internacionalizados (IDNS). Um nome de domínio internacionalizados é um nome de domínio que contém caracteres não-ASCII. Esse suporte inclui a capacidade de hospedar um serviço WCF com um nome IDN e um cliente WCF para se comunicar com um serviço web com um nome IDN.  
  
## <a name="systemuri-and-idn"></a>System. URI e IDN  
 <xref:System.Uri>tem duas propriedades <xref:System.Uri.Host%2A> e <xref:System.Uri.DnsSafeHost%2A>. Essas propriedades contêm valores Unicode ou Punycode, dependendo das configurações de configuração de IDN.  
  
 IDN está habilitada no arquivo de configuração de um aplicativo usando o seguinte XML  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All/AllExceptIntranet/None" />  
  </uri>  
</configuration>  
```  
  
 O \<idn > elemento contém o atributo enabled que pode ser definido como um dos valores a seguir:  
  
1.  "None"  
  
2.  "AllExceptIntranet"  
  
3.  "Todos"  
  
 Quando a configuração de IDN é definida como "None", nenhuma conversão é executada pelo URI ou DnsSafeHost. Quando a configuração de IDN é definida como uri "Todos". Host permanece Unicode e uri. DnsSafeHost é convertido em Punycode. Quando a configuração de IDN é definida como "AllExceptIntranet", o uri. DnsSafeHost é convertido em Punycode para endereços da internet e permanece Unicode para endereços da intranet. Essa configuração é importante para a resolução de nome DNS correta. Observe que essa configuração não deve ser configurado para Windows 8 e versões mais recentes.  
  
> [!WARNING]
>  Deve nunca codificar um endereço usando Punycode. WCF converterá para você com base nas definições de configuração que você aplicar.  
  
> [!WARNING]
>  Ao adicionar caracteres Unicode para applicationHost.exe.config, salve o arquivo usando a codificação UTF-8.  
  
## <a name="see-also"></a>Consulte também  
 [System. URI](http://msdn.microsoft.com/library/system.uri.aspx)
