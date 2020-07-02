---
ms.openlocfilehash: 0024b2a53444319788b8cdd312d537f994070b5e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614290"
---
### <a name="sslstream-supports-tls-alerts"></a><span data-ttu-id="bf328-101">SslStream dá suporte a Alertas de TLS</span><span class="sxs-lookup"><span data-stu-id="bf328-101">SslStream supports TLS Alerts</span></span>

#### <a name="details"></a><span data-ttu-id="bf328-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="bf328-102">Details</span></span>

<span data-ttu-id="bf328-103">Após um handshake de TLS com falha, um <xref:System.IO.IOException?displayProperty=fullName> com uma exceção <xref:System.ComponentModel.Win32Exception?displayProperty=fullName> interna será lançado pela primeira operação de Leitura/Gravação de E/S.</span><span class="sxs-lookup"><span data-stu-id="bf328-103">After a failed TLS handshake, an <xref:System.IO.IOException?displayProperty=fullName> with an inner <xref:System.ComponentModel.Win32Exception?displayProperty=fullName> exception will be thrown by the first I/O Read/Write operation.</span></span> <span data-ttu-id="bf328-104">O <xref:System.ComponentModel.Win32Exception.NativeErrorCode?displayProperty=fullName> código para o <xref:System.ComponentModel.Win32Exception?displayProperty=fullName> pode ser mapeado para o alerta TLS da parte remota usando os [códigos de erro Schannel para alertas TLS e SSL](https://docs.microsoft.com/windows/desktop/SecAuthN/schannel-error-codes-for-tls-and-ssl-alerts). Para obter mais informações, consulte [RFC 2246: seção 7.2.2 Error Alerts](https://tools.ietf.org/html/rfc2246#section-7.2.2).</span><span class="sxs-lookup"><span data-stu-id="bf328-104">The <xref:System.ComponentModel.Win32Exception.NativeErrorCode?displayProperty=fullName> code for the <xref:System.ComponentModel.Win32Exception?displayProperty=fullName> can be mapped to the TLS Alert from the remote party using the [Schannel error codes for TLS and SSL alerts](https://docs.microsoft.com/windows/desktop/SecAuthN/schannel-error-codes-for-tls-and-ssl-alerts).For more information, see [RFC 2246: Section 7.2.2 Error alerts](https://tools.ietf.org/html/rfc2246#section-7.2.2).</span></span> <br/><span data-ttu-id="bf328-105">O comportamento no .NET Framework 4.6.2 e nas versões anteriores é que o canal de transporte (normalmente a conexão TCP) atingirá o tempo limite durante a gravação ou a leitura se a outra parte falhar no handshake e rejeitar a conexão logo depois.</span><span class="sxs-lookup"><span data-stu-id="bf328-105">The behavior in .NET Framework 4.6.2 and earlier is that the transport channel (usually TCP connection) will timeout during either Write or Read if the other party failed the handshake and immediately afterwards rejected the connection.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="bf328-106">Sugestão</span><span class="sxs-lookup"><span data-stu-id="bf328-106">Suggestion</span></span>

<span data-ttu-id="bf328-107">Os aplicativos que chamam APIs de E/S de rede, como <xref:System.IO.Stream.Read(System.Byte[],System.Int32,System.Int32)>/<xref:System.IO.Stream.Write(System.Byte[],System.Int32,System.Int32)>, devem tratar <xref:System.IO.IOException> ou <xref:System.TimeoutException?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="bf328-107">Applications calling network I/O APIs such as <xref:System.IO.Stream.Read(System.Byte[],System.Int32,System.Int32)>/<xref:System.IO.Stream.Write(System.Byte[],System.Int32,System.Int32)> should handle <xref:System.IO.IOException> or <xref:System.TimeoutException?displayProperty=fullName>.</span></span><br/><span data-ttu-id="bf328-108">O recurso de Alertas TLS é habilitado por padrão, começando com o .NET Framework 4.7.</span><span class="sxs-lookup"><span data-stu-id="bf328-108">The TLS Alerts feature is enabled by default starting with .NET Framework 4.7.</span></span> <span data-ttu-id="bf328-109">Os aplicativos direcionados às versões 4.0 a 4.6.2 do .NET Framework em execução no .NET Framework 4.7 ou em um sistema superior terão o recurso desabilitado para preservar a compatibilidade.</span><span class="sxs-lookup"><span data-stu-id="bf328-109">Applications targeting versions of the .NET Framework from 4.0 through 4.6.2 running on a .NET Framework 4.7 or higher system will have the feature disabled to preserve compatibility.</span></span> <br/><span data-ttu-id="bf328-110">A API de configuração a seguir está disponível para habilitar ou desabilitar o recurso para os aplicativos do .NET Framework 4.6 e posteriores em execução no .NET Framework 4.7 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="bf328-110">The following configuration API is available to enable or disable the feature for .NET Framework 4.6 and later applications running on .NET Framework 4.7 or later.</span></span>

- <span data-ttu-id="bf328-111">Programaticamente: deve ser a primeira coisa que o aplicativo faz, pois ServicePointManager será inicializado apenas uma vez:</span><span class="sxs-lookup"><span data-stu-id="bf328-111">Programmatically:   Must be the very first thing the application does since ServicePointManager will initialize only once:</span></span>

    ```csharp
    AppContext.SetSwitch("TestSwitch.LocalAppContext.DisableCaching", true);

    // Set to 'false' to enable the feature in .NET Framework 4.6 - 4.6.2.
    AppContext.SetSwitch("Switch.System.Net.DontEnableTlsAlerts", true);
    ```

- <span data-ttu-id="bf328-112">AppConfig:</span><span class="sxs-lookup"><span data-stu-id="bf328-112">AppConfig:</span></span>

    ```xml
    <runtime>
      <AppContextSwitchOverrides value="Switch.System.Net.DontEnableTlsAlerts=true"/>
      <!-- Set to 'false' to enable the feature in .NET Framework 4.6 - 4.6.2. -->
    </runtime>
    ```

- <span data-ttu-id="bf328-113">Chave do registro (global do computador): defina o valor como `false` para habilitar o recurso no .NET Framework 4,6-4.6.2.</span><span class="sxs-lookup"><span data-stu-id="bf328-113">Registry key (machine global):   Set the Value to `false` to enable the feature in .NET Framework 4.6 - 4.6.2.</span></span>

    ```ini
    Key: HKLM\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\AppContext\Switch.System.Net.DontEnableTlsAlerts
    - Type: String
    - Value: "true"
    ```

| <span data-ttu-id="bf328-114">Name</span><span class="sxs-lookup"><span data-stu-id="bf328-114">Name</span></span>    | <span data-ttu-id="bf328-115">Valor</span><span class="sxs-lookup"><span data-stu-id="bf328-115">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="bf328-116">Escopo</span><span class="sxs-lookup"><span data-stu-id="bf328-116">Scope</span></span>   | <span data-ttu-id="bf328-117">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="bf328-117">Edge</span></span>        |
| <span data-ttu-id="bf328-118">Versão</span><span class="sxs-lookup"><span data-stu-id="bf328-118">Version</span></span> | <span data-ttu-id="bf328-119">4.7</span><span class="sxs-lookup"><span data-stu-id="bf328-119">4.7</span></span>         |
| <span data-ttu-id="bf328-120">Type</span><span class="sxs-lookup"><span data-stu-id="bf328-120">Type</span></span>    | <span data-ttu-id="bf328-121">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="bf328-121">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="bf328-122">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="bf328-122">Affected APIs</span></span>

- <xref:System.Net.Security.SslStream?displayProperty=nameWithType>
- <xref:System.Net.WebRequest?displayProperty=nameWithType>
- <xref:System.Net.HttpWebRequest?displayProperty=nameWithType>
- <xref:System.Net.FtpWebRequest?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Http?displayProperty=nameWithType>
