---
title: HttpListener
ms.date: 03/30/2017
helpviewer_keywords:
- HTTP
ms.assetid: 5b89d3fb-3c9a-49e2-af1f-c34c020c68ac
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: db2c42dab15b4282c5474c50f970ffe47a101215
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="httplistener"></a>HttpListener
A classe <xref:System.Net.HttpListener> fornece um ouvinte de protocolo HTTP controlado programaticamente. O ouvinte fica ativo durante o tempo de vida do objeto <xref:System.Net.HttpListener> e é executado dentro de seu aplicativo.  
  
## <a name="httpsys"></a>HTTP.SYS  
 A classe <xref:System.Net.HttpListener> é criada sobre HTTP.sys, que é o ouvinte de modo kernel que manipula todo o tráfego HTTP para o Windows. O HTTP.sys fornece gerenciamento de conexão, a limitação de largura de banda e registro em log do servidor Web. Use a ferramenta `HttpCfg.exe` para adicionar certificados SSL. Para obter mais informações, consulte a documentação sobre a ferramenta [HttpCfg.exe](http://go.microsoft.com/fwlink/?LinkID=178284) na documentação do [Servidor](http://go.microsoft.com/fwlink/?LinkID=178285).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Net.HttpListener>  
 <xref:System.Net.HttpWebRequest>  
 <xref:System.Net.HttpWebResponse>  
 [Servidor HTTP](http://go.microsoft.com/fwlink/?LinkID=178285)  
 [Melhorias de segurança em informações da Internet](http://go.microsoft.com/fwlink/?LinkID=178286)  
 [Amostra de aplicativo host ASPX HttpListener](http://go.microsoft.com/fwlink/?LinkID=179560)  
 [Amostra de tecnologia HttpListener](http://go.microsoft.com/fwlink/?LinkID=179558)  
 [Amostras de programação de rede](../../../docs/framework/network-programming/network-programming-samples.md)
