---
ms.openlocfilehash: 9fd4e570d9476f5ac4c310759113d72b354a3060
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90606879"
---
### <a name="tls-1x-by-default-passes-the-sch_send_aux_record-flag-to-the-underlying-schannel-api"></a><span data-ttu-id="7174a-101">TLS 1.x por padrão passa o sinalizador SCH_SEND_AUX_RECORD para a API do SCHANNEL subjacente</span><span class="sxs-lookup"><span data-stu-id="7174a-101">TLS 1.x by default passes the SCH_SEND_AUX_RECORD flag to the underlying SCHANNEL API</span></span>

#### <a name="details"></a><span data-ttu-id="7174a-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="7174a-102">Details</span></span>

<span data-ttu-id="7174a-103">Ao usar TLS 1.x, o .NET Framework depende da API de SCHANNEL do Windows subjacente.</span><span class="sxs-lookup"><span data-stu-id="7174a-103">When using TLS 1.x, the .NET Framework relies on the underlying Windows SCHANNEL API.</span></span> <span data-ttu-id="7174a-104">A partir do .NET Framework 4.6, o sinalizador [SCH_SEND_AUX_RECORD](/windows/win32/api/schannel/ns-schannel-schannel_cred) é passado por padrão para SCHANNEL.</span><span class="sxs-lookup"><span data-stu-id="7174a-104">Starting with .NET Framework 4.6, the [SCH_SEND_AUX_RECORD](/windows/win32/api/schannel/ns-schannel-schannel_cred) flag is passed by default to SCHANNEL.</span></span> <span data-ttu-id="7174a-105">Isso faz com que SCHANNEL divida os dados a serem criptografados em dois registros separados, o primeiro como um byte único e o segundo como <em>n</em>-1 bytes. Em casos raros, isso interrompe a comunicação entre clientes e servidores existentes que supõem que os dados residem em um único registro.</span><span class="sxs-lookup"><span data-stu-id="7174a-105">This causes SCHANNEL to split data to be encrypted into two separate records, the first as a single byte and the second as <em>n</em>-1 bytes.In rare cases, this breaks communication between clients and existing servers that make the assumption that the data resides in a single record.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="7174a-106">Sugestão</span><span class="sxs-lookup"><span data-stu-id="7174a-106">Suggestion</span></span>

<span data-ttu-id="7174a-107">Se essa alteração interromper a comunicação com um servidor existente, você poderá desabilitá-la enviando o sinalizador [SCH_SEND_AUX_RECORD](/windows/win32/api/schannel/ns-schannel-schannel_cred), e restaurar o comportamento anterior de não dividir dados em registros separados adicionando a seguinte opção ao elemento [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) na seção [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) do arquivo de configuração de aplicativo:</span><span class="sxs-lookup"><span data-stu-id="7174a-107">If this change breaks communication with an existing server, you can disable sending the [SCH_SEND_AUX_RECORD](/windows/win32/api/schannel/ns-schannel-schannel_cred) flag and restore the previous behavior of not splitting data into separate records by adding the following switch to the [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your app configuration file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Net.DontEnableSchSendAuxRecord=true" />
</runtime>
```

> [!IMPORTANT]
> <span data-ttu-id="7174a-108">Essa configuração é fornecida apenas para compatibilidade com versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="7174a-108">This setting is provided for backward compatibility only.</span></span> <span data-ttu-id="7174a-109">Caso contrário, seu uso não é recomendado.</span><span class="sxs-lookup"><span data-stu-id="7174a-109">Its use is otherwise not recommended.</span></span>

| <span data-ttu-id="7174a-110">Name</span><span class="sxs-lookup"><span data-stu-id="7174a-110">Name</span></span>    | <span data-ttu-id="7174a-111">Valor</span><span class="sxs-lookup"><span data-stu-id="7174a-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="7174a-112">Escopo</span><span class="sxs-lookup"><span data-stu-id="7174a-112">Scope</span></span>   | <span data-ttu-id="7174a-113">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="7174a-113">Edge</span></span>        |
| <span data-ttu-id="7174a-114">Versão</span><span class="sxs-lookup"><span data-stu-id="7174a-114">Version</span></span> | <span data-ttu-id="7174a-115">4.6</span><span class="sxs-lookup"><span data-stu-id="7174a-115">4.6</span></span>         |
| <span data-ttu-id="7174a-116">Tipo</span><span class="sxs-lookup"><span data-stu-id="7174a-116">Type</span></span>    | <span data-ttu-id="7174a-117">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="7174a-117">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="7174a-118">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="7174a-118">Affected APIs</span></span>

- <xref:System.Net.Security.SslStream?displayProperty=nameWithType>
- <xref:System.Net.ServicePointManager?displayProperty=nameWithType>
- <xref:System.Net.Http.HttpClient?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.HttpWebRequest?displayProperty=nameWithType>
- <xref:System.Net.FtpWebRequest?displayProperty=nameWithType>
