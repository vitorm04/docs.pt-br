---
title: Criando solicitações da Internet
ms.date: 03/30/2017
helpviewer_keywords:
- WebRequest class, sending and receiving data
- Networking
- HttpWebResponse class, sending and receiving data
- requesting data from Internet, creating requests
- Network Resources
- Internet, requesting data
- data requests, creating requests
ms.assetid: faab683e-3f1e-4eee-b5e9-59f7245033d5
ms.openlocfilehash: 80e3a6bd199691df9391e88d5a64fab5df2a08a1
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048616"
---
# <a name="creating-internet-requests"></a>Criando solicitações da Internet
Os aplicativos criam instâncias <xref:System.Net.WebRequest> por meio do método <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType>. Este é um método estático que cria uma classe derivada de **WebRequest**, com base no esquema de URI passado para ele.  
  
## <a name="web-file-and-ftp-requests"></a>Solicitações da Web, de arquivo e de FTP  
 O .NET Framework fornece a classe <xref:System.Net.HttpWebRequest>, que é derivada de **WebRequest**, para manipular solicitações HTTP e HTTPS. Na maioria dos casos, a classe **WebRequest** fornece todas as propriedades necessárias para fazer uma solicitação; no entanto, se necessário, é possível converter objetos **WebRequest** criados pelo método **WebRequest.Create** no tipo **HttpWebRequest** para acessar as propriedades específicas de HTTP da solicitação. Da mesma forma, o objeto **HttpWebResponse** manipula as respostas das solicitações HTTP e HTTPS. Para acessar as propriedades específicas de HTTP do objeto **HttpWebResponse**, é necessário converter objetos **WebResponse** no tipo **HttpWebResponse**.  
  
 O .NET Framework também fornece as classes <xref:System.Net.FileWebRequest> e <xref:System.Net.FileWebResponse> para manipular solicitações para recursos que usam o esquema de URI "file:" . Da mesma forma, as classes <xref:System.Net.FtpWebRequest> e <xref:System.Net.FtpWebResponse> são fornecidas para manipular solicitações para recursos que usam o esquema “ftp:”. Se a solicitação for para um recurso que usa um desses esquemas, use o método **WebRequest.Create** para obter um objeto com o qual a solicitação será feita.  
  
 Para manipular solicitações que usam outros protocolos no nível de aplicativo, é necessário implementar classes específicas ao protocolo derivadas de **WebRequest** e **WebResponse**. Para obter mais informações, consulte [Programando protocolos conectáveis](programming-pluggable-protocols.md).  
  
## <a name="see-also"></a>Consulte também

- [Como: Solicitar dados usando a classe WebRequest](how-to-request-data-using-the-webrequest-class.md)
- [Solicitando dados](requesting-data.md)
