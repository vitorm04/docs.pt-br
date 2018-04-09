## <a name="introduction"></a>Introdução
As alterações de redirecionamento afetam aplicativos que estão recompilados para direcionarem um .NET Framework diferente. Entre elas estão:

* Alterações feitas no ambiente de tempo de design. Por exemplo, as ferramentas de compilação podem emitir avisos quando antes não faziam isso.

* Alterações feitas no ambiente de tempo de execução. Elas afetam apenas os aplicativos que direcionam especificamente o .NET Framework redirecionado. Os aplicativos destinados a versões anteriores do .NET Framework se comportam como antes durante a execução nessas versões.

Nos tópicos que descrevem alterações de redirecionamento, classificamos itens individuais pelo impacto esperado, da seguinte forma:

**Principal** Essa é uma alteração significativa que afeta um grande número de aplicativos ou que exige a modificação significativa do código.

**Secundária** Essa é uma alteração que afeta um pequeno número de aplicativos ou que exige a modificação secundária do código.

**Caso de borda** Essa é uma alteração que afeta aplicativos em cenários muito específicos que não são comuns.

**Transparente** Essa é uma alteração que não tem efeito visível para o desenvolvedor ou o usuário do aplicativo. O aplicativo não deve exigir modificação por conta dessa alteração.
