---
ms.openlocfilehash: d312ba2a22797ff6afff6b893f998c965e68e86e
ms.sourcegitcommit: e078b7540a8293ca1b604c9c0da1ff1506f0170b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/13/2020
ms.locfileid: "91997749"
---
### <a name="default-tls-cipher-suites-for-net-on-linux"></a><span data-ttu-id="3a93a-101">Conjuntos de codificação TLS padrão para .NET no Linux</span><span class="sxs-lookup"><span data-stu-id="3a93a-101">Default TLS cipher suites for .NET on Linux</span></span>

<span data-ttu-id="3a93a-102">O .NET, no Linux, agora respeita a configuração do OpenSSL para conjuntos de codificação padrão ao fazer o TLS/SSL por meio de <xref:System.Net.Security.SslStream> operações de nível superior ou de classe, como https por meio da <xref:System.Net.Http.HttpClient> classe.</span><span class="sxs-lookup"><span data-stu-id="3a93a-102">.NET, on Linux, now respects the OpenSSL configuration for default cipher suites when doing TLS/SSL via the <xref:System.Net.Security.SslStream> class or higher-level operations, such as HTTPS via the <xref:System.Net.Http.HttpClient> class.</span></span> <span data-ttu-id="3a93a-103">Quando os conjuntos de codificação padrão não são explicitamente configurados, o .NET no Linux usa uma lista rigorosamente restrita de conjuntos de codificação permitidos.</span><span class="sxs-lookup"><span data-stu-id="3a93a-103">When default cipher suites aren't explicitly configured, .NET on Linux uses a tightly restricted list of permitted cipher suites.</span></span>

#### <a name="change-description"></a><span data-ttu-id="3a93a-104">Descrição das alterações</span><span class="sxs-lookup"><span data-stu-id="3a93a-104">Change description</span></span>

<span data-ttu-id="3a93a-105">Nas versões anteriores do .NET, o .NET não respeita a configuração do sistema para conjuntos de codificação padrão.</span><span class="sxs-lookup"><span data-stu-id="3a93a-105">In previous .NET versions, .NET does not respect system configuration for default cipher suites.</span></span> <span data-ttu-id="3a93a-106">A lista do pacote de criptografia padrão para .NET no Linux é muito permissiva.</span><span class="sxs-lookup"><span data-stu-id="3a93a-106">The default cipher suite list for .NET on Linux is very permissive.</span></span>

<span data-ttu-id="3a93a-107">A partir do .NET 5,0, o .NET no Linux respeita a configuração do OpenSSL para conjuntos de codificação padrão quando ele é especificado no *OpenSSL. cnf*.</span><span class="sxs-lookup"><span data-stu-id="3a93a-107">Starting in .NET 5.0, .NET on Linux respects the OpenSSL configuration for default cipher suites when it's specified in *openssl.cnf*.</span></span> <span data-ttu-id="3a93a-108">Quando os conjuntos de codificação não são explicitamente configurados, os únicos conjuntos de codificação permitidos são os seguintes:</span><span class="sxs-lookup"><span data-stu-id="3a93a-108">When cipher suites aren't explicitly configured, the only permitted cipher suites are as follows:</span></span>

- <span data-ttu-id="3a93a-109">Pacotes de criptografia TLS 1,3</span><span class="sxs-lookup"><span data-stu-id="3a93a-109">TLS 1.3 cipher suites</span></span>
- <span data-ttu-id="3a93a-110">TLS_ECDHE_ECDSA_WITH_AES_256_GCM_SHA384</span><span class="sxs-lookup"><span data-stu-id="3a93a-110">TLS_ECDHE_ECDSA_WITH_AES_256_GCM_SHA384</span></span>
- <span data-ttu-id="3a93a-111">TLS_ECDHE_ECDSA_WITH_AES_128_GCM_SHA256</span><span class="sxs-lookup"><span data-stu-id="3a93a-111">TLS_ECDHE_ECDSA_WITH_AES_128_GCM_SHA256</span></span>
- <span data-ttu-id="3a93a-112">TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384</span><span class="sxs-lookup"><span data-stu-id="3a93a-112">TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384</span></span>
- <span data-ttu-id="3a93a-113">TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256</span><span class="sxs-lookup"><span data-stu-id="3a93a-113">TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256</span></span>
- <span data-ttu-id="3a93a-114">TLS_ECDHE_ECDSA_WITH_AES_256_CBC_SHA384</span><span class="sxs-lookup"><span data-stu-id="3a93a-114">TLS_ECDHE_ECDSA_WITH_AES_256_CBC_SHA384</span></span>
- <span data-ttu-id="3a93a-115">TLS_ECDHE_ECDSA_WITH_AES_128_CBC_SHA256</span><span class="sxs-lookup"><span data-stu-id="3a93a-115">TLS_ECDHE_ECDSA_WITH_AES_128_CBC_SHA256</span></span>
- <span data-ttu-id="3a93a-116">TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA384</span><span class="sxs-lookup"><span data-stu-id="3a93a-116">TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA384</span></span>
- <span data-ttu-id="3a93a-117">TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA256</span><span class="sxs-lookup"><span data-stu-id="3a93a-117">TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA256</span></span>

<span data-ttu-id="3a93a-118">Como esse padrão de fallback não inclui conjuntos de codificação compatíveis com TLS 1,0 ou TLS 1,1, essas versões de protocolo mais antigas são efetivamente desabilitadas por padrão.</span><span class="sxs-lookup"><span data-stu-id="3a93a-118">Since this fallback default doesn't include any cipher suites that are compatible with TLS 1.0 or TLS 1.1, these older protocol versions are effectively disabled by default.</span></span>

<span data-ttu-id="3a93a-119">O fornecimento de um valor de CipherSuitePolicy para SslStream para uma sessão específica ainda substituirá o conteúdo do arquivo de configuração e/ou o padrão de fallback do .NET.</span><span class="sxs-lookup"><span data-stu-id="3a93a-119">Supplying a CipherSuitePolicy value to SslStream for a specific session will still replace the configuration file content and/or .NET fallback default.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="3a93a-120">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="3a93a-120">Reason for change</span></span>

<span data-ttu-id="3a93a-121">Os usuários que executam o .NET no Linux solicitaram que a configuração padrão <xref:System.Net.Security.SslStream> seja alterada para uma que fornecesse uma alta classificação de segurança de ferramentas de avaliação de terceiros.</span><span class="sxs-lookup"><span data-stu-id="3a93a-121">Users running .NET on Linux requested that the default configuration for <xref:System.Net.Security.SslStream> be changed to one that provided a high security rating from third-party assessment tools.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="3a93a-122">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="3a93a-122">Version introduced</span></span>

<span data-ttu-id="3a93a-123">RC1 5,0</span><span class="sxs-lookup"><span data-stu-id="3a93a-123">5.0 RC1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="3a93a-124">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="3a93a-124">Recommended action</span></span>

<span data-ttu-id="3a93a-125">Os novos padrões provavelmente funcionarão ao se comunicar com clientes ou servidores modernos.</span><span class="sxs-lookup"><span data-stu-id="3a93a-125">The new defaults are likely to work when communicating with modern clients or servers.</span></span> <span data-ttu-id="3a93a-126">Se você precisar expandir a lista padrão de pacotes de criptografia para aceitar clientes herdados (ou contatar servidores herdados), especifique um `CipherSuitePolicy` valor ou altere o arquivo de configuração do OpenSSL.</span><span class="sxs-lookup"><span data-stu-id="3a93a-126">If you need to expand the default cipher suite list to accept legacy clients (or to contact legacy servers), either specify a `CipherSuitePolicy` value or change the OpenSSL configuration file.</span></span> <span data-ttu-id="3a93a-127">Em muitas distribuições do Linux, o arquivo de configuração do OpenSSL está em */etc/SSL/OpenSSL.cnf*.</span><span class="sxs-lookup"><span data-stu-id="3a93a-127">On many Linux distributions, the OpenSSL configuration file is at */etc/ssl/openssl.cnf*.</span></span>

<span data-ttu-id="3a93a-128">Este arquivo *OpenSSL. cnf* de exemplo é um arquivo mínimo equivalente à política de pacotes de criptografia padrão para o .NET 5,0 e posterior no Linux.</span><span class="sxs-lookup"><span data-stu-id="3a93a-128">This sample *openssl.cnf* file is a minimal file that's equivalent to the default cipher suites policy for .NET 5.0 and later on Linux.</span></span> <span data-ttu-id="3a93a-129">Em vez de substituir o arquivo do sistema, mescle esses conceitos com o arquivo que está presente no seu sistema.</span><span class="sxs-lookup"><span data-stu-id="3a93a-129">Instead of replacing the system file, merge these concepts with the file that's present on your system.</span></span>

```ini
openssl_conf = default_conf

[default_conf]
ssl_conf = ssl_sect

[ssl_sect]
system_default = system_default_sect

[system_default_sect]
CipherString = ECDHE-ECDSA-AES256-GCM-SHA384:ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-RSA-AES256-GCM-SHA384:ECDHE-RSA-AES128-GCM-SHA256:ECDHE-ECDSA-AES256-SHA384:ECDHE-ECDSA-AES128-SHA256:ECDHE-RSA-AES256-SHA384:ECDHE-RSA-AES128-SHA256
```

<span data-ttu-id="3a93a-130">Nas distribuições Red Hat Enterprise Linux, CentOS e Fedora, os aplicativos .NET assumem como padrão os conjuntos de codificação permitidos pelas políticas de criptografia de todo o sistema.</span><span class="sxs-lookup"><span data-stu-id="3a93a-130">On the Red Hat Enterprise Linux, CentOS, and Fedora distributions, .NET applications default to the cipher suites permitted by the system-wide cryptographic policies.</span></span> <span data-ttu-id="3a93a-131">Nessas distribuições, use a configuração de políticas de criptografia em vez do *OpenSSL. cnf*.</span><span class="sxs-lookup"><span data-stu-id="3a93a-131">On these distributions, use the crypto-policies configuration instead of *openssl.cnf*.</span></span>

#### <a name="category"></a><span data-ttu-id="3a93a-132">Categoria</span><span class="sxs-lookup"><span data-stu-id="3a93a-132">Category</span></span>

- <span data-ttu-id="3a93a-133">Criptografia</span><span class="sxs-lookup"><span data-stu-id="3a93a-133">Cryptography</span></span>
- <span data-ttu-id="3a93a-134">Segurança</span><span class="sxs-lookup"><span data-stu-id="3a93a-134">Security</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="3a93a-135">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="3a93a-135">Affected APIs</span></span>

<span data-ttu-id="3a93a-136">Não detectible por meio da análise de API.</span><span class="sxs-lookup"><span data-stu-id="3a93a-136">Not detectible via API analysis.</span></span>

<!--

#### Affected APIs

- Not detectible via API analysis.

-->
