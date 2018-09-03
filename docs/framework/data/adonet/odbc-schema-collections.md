---
title: Coleções de esquema ODBC
ms.date: 03/30/2017
ms.assetid: 1bb126a5-ceec-4649-a4bc-8aa19e801046
ms.openlocfilehash: bdedbb11960f02b99dcca6388abf663635238f74
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43479974"
---
# <a name="odbc-schema-collections"></a><span data-ttu-id="55b79-102">Coleções de esquema ODBC</span><span class="sxs-lookup"><span data-stu-id="55b79-102">ODBC Schema Collections</span></span>
<span data-ttu-id="55b79-103">Esta seção discute o suporte de coleção de esquema para os drivers ODBC para Microsoft SQL Server, Oracle e Microsoft Jet.</span><span class="sxs-lookup"><span data-stu-id="55b79-103">This section discusses schema collection support for the ODBC drivers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-odbc-driver"></a><span data-ttu-id="55b79-104">Driver ODBC do Microsoft SQL Server</span><span class="sxs-lookup"><span data-stu-id="55b79-104">Microsoft SQL Server ODBC Driver</span></span>  
 <span data-ttu-id="55b79-105">O Driver ODBC do Microsoft SQL Server suporta as seguintes coleções de esquema específico, além das coleções de esquema comuns:</span><span class="sxs-lookup"><span data-stu-id="55b79-105">The Microsoft SQL Server ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="55b79-106">Tabelas</span><span class="sxs-lookup"><span data-stu-id="55b79-106">Tables</span></span>  
  
-   <span data-ttu-id="55b79-107">Índices</span><span class="sxs-lookup"><span data-stu-id="55b79-107">Indexes</span></span>  
  
-   <span data-ttu-id="55b79-108">Colunas</span><span class="sxs-lookup"><span data-stu-id="55b79-108">Columns</span></span>  
  
-   <span data-ttu-id="55b79-109">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="55b79-109">Procedures</span></span>  
  
-   <span data-ttu-id="55b79-110">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="55b79-110">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="55b79-111">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="55b79-111">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="55b79-112">Exibições</span><span class="sxs-lookup"><span data-stu-id="55b79-112">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="55b79-113">Tabelas e exibições</span><span class="sxs-lookup"><span data-stu-id="55b79-113">Tables and Views</span></span>  
  
|<span data-ttu-id="55b79-114">ColumnName</span><span class="sxs-lookup"><span data-stu-id="55b79-114">ColumnName</span></span>|<span data-ttu-id="55b79-115">DataType</span><span class="sxs-lookup"><span data-stu-id="55b79-115">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="55b79-116">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="55b79-116">TABLE_CAT</span></span>|<span data-ttu-id="55b79-117">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-117">String</span></span>|  
|<span data-ttu-id="55b79-118">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="55b79-118">TABLE_SCHEM</span></span>|<span data-ttu-id="55b79-119">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-119">String</span></span>|  
|<span data-ttu-id="55b79-120">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="55b79-120">TABLE_NAME</span></span>|<span data-ttu-id="55b79-121">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-121">String</span></span>|  
|<span data-ttu-id="55b79-122">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="55b79-122">TABLE_TYPE</span></span>|<span data-ttu-id="55b79-123">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-123">String</span></span>|  
|<span data-ttu-id="55b79-124">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="55b79-124">REMARKS</span></span>|<span data-ttu-id="55b79-125">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-125">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="55b79-126">Índices</span><span class="sxs-lookup"><span data-stu-id="55b79-126">Indexes</span></span>  
  
|<span data-ttu-id="55b79-127">ColumnName</span><span class="sxs-lookup"><span data-stu-id="55b79-127">ColumnName</span></span>|<span data-ttu-id="55b79-128">DataType</span><span class="sxs-lookup"><span data-stu-id="55b79-128">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="55b79-129">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="55b79-129">TABLE_CAT</span></span>|<span data-ttu-id="55b79-130">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-130">String</span></span>|  
|<span data-ttu-id="55b79-131">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="55b79-131">TABLE_SCHEM</span></span>|<span data-ttu-id="55b79-132">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-132">String</span></span>|  
|<span data-ttu-id="55b79-133">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="55b79-133">TABLE_NAME</span></span>|<span data-ttu-id="55b79-134">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-134">String</span></span>|  
|<span data-ttu-id="55b79-135">NON_UNIQUE</span><span class="sxs-lookup"><span data-stu-id="55b79-135">NON_UNIQUE</span></span>|<span data-ttu-id="55b79-136">Int16</span><span class="sxs-lookup"><span data-stu-id="55b79-136">Int16</span></span>|  
|<span data-ttu-id="55b79-137">INDEX_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="55b79-137">INDEX_QUALIFIER</span></span>|<span data-ttu-id="55b79-138">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-138">String</span></span>|  
|<span data-ttu-id="55b79-139">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="55b79-139">INDEX_NAME</span></span>|<span data-ttu-id="55b79-140">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-140">String</span></span>|  
|<span data-ttu-id="55b79-141">TIPO</span><span class="sxs-lookup"><span data-stu-id="55b79-141">TYPE</span></span>|<span data-ttu-id="55b79-142">Int16</span><span class="sxs-lookup"><span data-stu-id="55b79-142">Int16</span></span>|  
|<span data-ttu-id="55b79-143">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="55b79-143">ORDINAL_POSITION</span></span>|<span data-ttu-id="55b79-144">Int16</span><span class="sxs-lookup"><span data-stu-id="55b79-144">Int16</span></span>|  
|<span data-ttu-id="55b79-145">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="55b79-145">COLUMN_NAME</span></span>|<span data-ttu-id="55b79-146">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-146">String</span></span>|  
|<span data-ttu-id="55b79-147">ASC_OR_DESC</span><span class="sxs-lookup"><span data-stu-id="55b79-147">ASC_OR_DESC</span></span>|<span data-ttu-id="55b79-148">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-148">String</span></span>|  
|<span data-ttu-id="55b79-149">CARDINALIDADE</span><span class="sxs-lookup"><span data-stu-id="55b79-149">CARDINATLITY</span></span>|<span data-ttu-id="55b79-150">Int32</span><span class="sxs-lookup"><span data-stu-id="55b79-150">Int32</span></span>|  
|<span data-ttu-id="55b79-151">PÁGINAS</span><span class="sxs-lookup"><span data-stu-id="55b79-151">PAGES</span></span>|<span data-ttu-id="55b79-152">Int32</span><span class="sxs-lookup"><span data-stu-id="55b79-152">Int32</span></span>|  
|<span data-ttu-id="55b79-153">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="55b79-153">FILTER_CONDITION</span></span>|<span data-ttu-id="55b79-154">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-154">String</span></span>|  
|<span data-ttu-id="55b79-155">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="55b79-155">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="55b79-156">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-156">String</span></span>|  
|<span data-ttu-id="55b79-157">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="55b79-157">SS_DATA_TYPE</span></span>|<span data-ttu-id="55b79-158">Byte</span><span class="sxs-lookup"><span data-stu-id="55b79-158">Byte</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="55b79-159">Colunas</span><span class="sxs-lookup"><span data-stu-id="55b79-159">Columns</span></span>  
  
|<span data-ttu-id="55b79-160">ColumnName</span><span class="sxs-lookup"><span data-stu-id="55b79-160">ColumnName</span></span>|<span data-ttu-id="55b79-161">DataType</span><span class="sxs-lookup"><span data-stu-id="55b79-161">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="55b79-162">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="55b79-162">TABLE_CAT</span></span>|<span data-ttu-id="55b79-163">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-163">String</span></span>|  
|<span data-ttu-id="55b79-164">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="55b79-164">TABLE_SCHEM</span></span>|<span data-ttu-id="55b79-165">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-165">String</span></span>|  
|<span data-ttu-id="55b79-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="55b79-166">TABLE_NAME</span></span>|<span data-ttu-id="55b79-167">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-167">String</span></span>|  
|<span data-ttu-id="55b79-168">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="55b79-168">COLUMN_NAME</span></span>|<span data-ttu-id="55b79-169">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-169">String</span></span>|  
|<span data-ttu-id="55b79-170">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="55b79-170">DATA_TYPE</span></span>|<span data-ttu-id="55b79-171">Int16</span><span class="sxs-lookup"><span data-stu-id="55b79-171">Int16</span></span>|  
|<span data-ttu-id="55b79-172">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="55b79-172">TYPE_NAME</span></span>|<span data-ttu-id="55b79-173">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-173">String</span></span>|  
|<span data-ttu-id="55b79-174">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="55b79-174">COLUMN_SIZE</span></span>|<span data-ttu-id="55b79-175">Int32</span><span class="sxs-lookup"><span data-stu-id="55b79-175">Int32</span></span>|  
|<span data-ttu-id="55b79-176">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="55b79-176">BUFFER_LENGTH</span></span>|<span data-ttu-id="55b79-177">Int32</span><span class="sxs-lookup"><span data-stu-id="55b79-177">Int32</span></span>|  
|<span data-ttu-id="55b79-178">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="55b79-178">DECIMAL_DIGITS</span></span>|<span data-ttu-id="55b79-179">Int16</span><span class="sxs-lookup"><span data-stu-id="55b79-179">Int16</span></span>|  
|<span data-ttu-id="55b79-180">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="55b79-180">NUM_PREC_RADIX</span></span>|<span data-ttu-id="55b79-181">Int16</span><span class="sxs-lookup"><span data-stu-id="55b79-181">Int16</span></span>|  
|<span data-ttu-id="55b79-182">PERMITE VALOR NULO</span><span class="sxs-lookup"><span data-stu-id="55b79-182">NULLABLE</span></span>|<span data-ttu-id="55b79-183">Int16</span><span class="sxs-lookup"><span data-stu-id="55b79-183">Int16</span></span>|  
|<span data-ttu-id="55b79-184">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="55b79-184">REMARKS</span></span>|<span data-ttu-id="55b79-185">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-185">String</span></span>|  
|<span data-ttu-id="55b79-186">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="55b79-186">COLUMN_DEF</span></span>|<span data-ttu-id="55b79-187">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-187">String</span></span>|  
|<span data-ttu-id="55b79-188">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="55b79-188">SQL_DATA_TYPE</span></span>|<span data-ttu-id="55b79-189">Int16</span><span class="sxs-lookup"><span data-stu-id="55b79-189">Int16</span></span>|  
|<span data-ttu-id="55b79-190">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="55b79-190">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="55b79-191">Int16</span><span class="sxs-lookup"><span data-stu-id="55b79-191">Int16</span></span>|  
|<span data-ttu-id="55b79-192">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="55b79-192">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="55b79-193">Int32</span><span class="sxs-lookup"><span data-stu-id="55b79-193">Int32</span></span>|  
|<span data-ttu-id="55b79-194">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="55b79-194">ORDINAL_POSITION</span></span>|<span data-ttu-id="55b79-195">Int32</span><span class="sxs-lookup"><span data-stu-id="55b79-195">Int32</span></span>|  
|<span data-ttu-id="55b79-196">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="55b79-196">IS_NULLABLE</span></span>|<span data-ttu-id="55b79-197">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-197">String</span></span>|  
|<span data-ttu-id="55b79-198">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="55b79-198">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="55b79-199">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-199">String</span></span>|  
|<span data-ttu-id="55b79-200">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="55b79-200">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="55b79-201">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-201">String</span></span>|  
|<span data-ttu-id="55b79-202">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="55b79-202">SS_DATA_TYPE</span></span>|<span data-ttu-id="55b79-203">Byte</span><span class="sxs-lookup"><span data-stu-id="55b79-203">Byte</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="55b79-204">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="55b79-204">Procedures</span></span>  
  
|<span data-ttu-id="55b79-205">ColumnName</span><span class="sxs-lookup"><span data-stu-id="55b79-205">ColumnName</span></span>|<span data-ttu-id="55b79-206">DataType</span><span class="sxs-lookup"><span data-stu-id="55b79-206">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="55b79-207">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="55b79-207">PROCEDURE_CAT</span></span>|<span data-ttu-id="55b79-208">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-208">String</span></span>|  
|<span data-ttu-id="55b79-209">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="55b79-209">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="55b79-210">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-210">String</span></span>|  
|<span data-ttu-id="55b79-211">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="55b79-211">PROCEDURE_NAME</span></span>|<span data-ttu-id="55b79-212">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-212">String</span></span>|  
|<span data-ttu-id="55b79-213">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="55b79-213">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="55b79-214">Int32</span><span class="sxs-lookup"><span data-stu-id="55b79-214">Int32</span></span>|  
|<span data-ttu-id="55b79-215">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="55b79-215">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="55b79-216">Int32</span><span class="sxs-lookup"><span data-stu-id="55b79-216">Int32</span></span>|  
|<span data-ttu-id="55b79-217">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="55b79-217">NUM_RESULT_SETS</span></span>|<span data-ttu-id="55b79-218">Int32</span><span class="sxs-lookup"><span data-stu-id="55b79-218">Int32</span></span>|  
|<span data-ttu-id="55b79-219">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="55b79-219">REMARKS</span></span>|<span data-ttu-id="55b79-220">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-220">String</span></span>|  
|<span data-ttu-id="55b79-221">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="55b79-221">PROCEDURE_TYPE</span></span>|<span data-ttu-id="55b79-222">Int16</span><span class="sxs-lookup"><span data-stu-id="55b79-222">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="55b79-223">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="55b79-223">ProcedureColumns</span></span>  
  
|<span data-ttu-id="55b79-224">ColumnName</span><span class="sxs-lookup"><span data-stu-id="55b79-224">ColumnName</span></span>|<span data-ttu-id="55b79-225">DataType</span><span class="sxs-lookup"><span data-stu-id="55b79-225">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="55b79-226">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="55b79-226">PROCEDURE_CAT</span></span>|<span data-ttu-id="55b79-227">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-227">String</span></span>|  
|<span data-ttu-id="55b79-228">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="55b79-228">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="55b79-229">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-229">String</span></span>|  
|<span data-ttu-id="55b79-230">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="55b79-230">PROCEDURE_NAME</span></span>|<span data-ttu-id="55b79-231">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-231">String</span></span>|  
|<span data-ttu-id="55b79-232">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="55b79-232">COLUMN_NAME</span></span>|<span data-ttu-id="55b79-233">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-233">String</span></span>|  
|<span data-ttu-id="55b79-234">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="55b79-234">COLUMN_TYPE</span></span>|<span data-ttu-id="55b79-235">Int16</span><span class="sxs-lookup"><span data-stu-id="55b79-235">Int16</span></span>|  
|<span data-ttu-id="55b79-236">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="55b79-236">DATA_TYPE</span></span>|<span data-ttu-id="55b79-237">Int16</span><span class="sxs-lookup"><span data-stu-id="55b79-237">Int16</span></span>|  
|<span data-ttu-id="55b79-238">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="55b79-238">TYPE_NAME</span></span>|<span data-ttu-id="55b79-239">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-239">String</span></span>|  
|<span data-ttu-id="55b79-240">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="55b79-240">COLUMN_SIZE</span></span>|<span data-ttu-id="55b79-241">Int32</span><span class="sxs-lookup"><span data-stu-id="55b79-241">Int32</span></span>|  
|<span data-ttu-id="55b79-242">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="55b79-242">BUFFER_LENGTH</span></span>|<span data-ttu-id="55b79-243">Int32</span><span class="sxs-lookup"><span data-stu-id="55b79-243">Int32</span></span>|  
|<span data-ttu-id="55b79-244">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="55b79-244">DECIMAL_DIGITS</span></span>|<span data-ttu-id="55b79-245">Int16</span><span class="sxs-lookup"><span data-stu-id="55b79-245">Int16</span></span>|  
|<span data-ttu-id="55b79-246">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="55b79-246">NUM_PREC_RADIX</span></span>|<span data-ttu-id="55b79-247">Int16</span><span class="sxs-lookup"><span data-stu-id="55b79-247">Int16</span></span>|  
|<span data-ttu-id="55b79-248">PERMITE VALOR NULO</span><span class="sxs-lookup"><span data-stu-id="55b79-248">NULLABLE</span></span>|<span data-ttu-id="55b79-249">Int16</span><span class="sxs-lookup"><span data-stu-id="55b79-249">Int16</span></span>|  
|<span data-ttu-id="55b79-250">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="55b79-250">REMARKS</span></span>|<span data-ttu-id="55b79-251">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-251">String</span></span>|  
|<span data-ttu-id="55b79-252">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="55b79-252">COLUMN_DEF</span></span>|<span data-ttu-id="55b79-253">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-253">String</span></span>|  
|<span data-ttu-id="55b79-254">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="55b79-254">SQL_DATA_TYPE</span></span>|<span data-ttu-id="55b79-255">Int16</span><span class="sxs-lookup"><span data-stu-id="55b79-255">Int16</span></span>|  
|<span data-ttu-id="55b79-256">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="55b79-256">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="55b79-257">Int16</span><span class="sxs-lookup"><span data-stu-id="55b79-257">Int16</span></span>|  
|<span data-ttu-id="55b79-258">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="55b79-258">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="55b79-259">Int32</span><span class="sxs-lookup"><span data-stu-id="55b79-259">Int32</span></span>|  
|<span data-ttu-id="55b79-260">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="55b79-260">ORDINAL_POSITION</span></span>|<span data-ttu-id="55b79-261">Int32</span><span class="sxs-lookup"><span data-stu-id="55b79-261">Int32</span></span>|  
|<span data-ttu-id="55b79-262">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="55b79-262">IS_NULLABLE</span></span>|<span data-ttu-id="55b79-263">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-263">String</span></span>|  
|<span data-ttu-id="55b79-264">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="55b79-264">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="55b79-265">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-265">String</span></span>|  
|<span data-ttu-id="55b79-266">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="55b79-266">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="55b79-267">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-267">String</span></span>|  
|<span data-ttu-id="55b79-268">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="55b79-268">SS_DATA_TYPE</span></span>|<span data-ttu-id="55b79-269">Byte</span><span class="sxs-lookup"><span data-stu-id="55b79-269">Byte</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="55b79-270">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="55b79-270">ProcedureParameters</span></span>  
  
|<span data-ttu-id="55b79-271">ColumnName</span><span class="sxs-lookup"><span data-stu-id="55b79-271">ColumnName</span></span>|<span data-ttu-id="55b79-272">DataType</span><span class="sxs-lookup"><span data-stu-id="55b79-272">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="55b79-273">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="55b79-273">PROCEDURE_CAT</span></span>|<span data-ttu-id="55b79-274">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-274">String</span></span>|  
|<span data-ttu-id="55b79-275">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="55b79-275">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="55b79-276">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-276">String</span></span>|  
|<span data-ttu-id="55b79-277">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="55b79-277">PROCEDURE_NAME</span></span>|<span data-ttu-id="55b79-278">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-278">String</span></span>|  
|<span data-ttu-id="55b79-279">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="55b79-279">COLUMN_NAME</span></span>|<span data-ttu-id="55b79-280">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-280">String</span></span>|  
|<span data-ttu-id="55b79-281">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="55b79-281">COLUMN_TYPE</span></span>|<span data-ttu-id="55b79-282">Int16</span><span class="sxs-lookup"><span data-stu-id="55b79-282">Int16</span></span>|  
|<span data-ttu-id="55b79-283">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="55b79-283">DATA_TYPE</span></span>|<span data-ttu-id="55b79-284">Int16</span><span class="sxs-lookup"><span data-stu-id="55b79-284">Int16</span></span>|  
|<span data-ttu-id="55b79-285">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="55b79-285">TYPE_NAME</span></span>|<span data-ttu-id="55b79-286">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-286">String</span></span>|  
|<span data-ttu-id="55b79-287">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="55b79-287">COLUMN_SIZE</span></span>|<span data-ttu-id="55b79-288">Int32</span><span class="sxs-lookup"><span data-stu-id="55b79-288">Int32</span></span>|  
|<span data-ttu-id="55b79-289">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="55b79-289">BUFFER_LENGTH</span></span>|<span data-ttu-id="55b79-290">Int32</span><span class="sxs-lookup"><span data-stu-id="55b79-290">Int32</span></span>|  
|<span data-ttu-id="55b79-291">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="55b79-291">DECIMAL_DIGITS</span></span>|<span data-ttu-id="55b79-292">Int16</span><span class="sxs-lookup"><span data-stu-id="55b79-292">Int16</span></span>|  
|<span data-ttu-id="55b79-293">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="55b79-293">NUM_PREC_RADIX</span></span>|<span data-ttu-id="55b79-294">Int16</span><span class="sxs-lookup"><span data-stu-id="55b79-294">Int16</span></span>|  
|<span data-ttu-id="55b79-295">PERMITE VALOR NULO</span><span class="sxs-lookup"><span data-stu-id="55b79-295">NULLABLE</span></span>|<span data-ttu-id="55b79-296">Int16</span><span class="sxs-lookup"><span data-stu-id="55b79-296">Int16</span></span>|  
|<span data-ttu-id="55b79-297">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="55b79-297">REMARKS</span></span>|<span data-ttu-id="55b79-298">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-298">String</span></span>|  
|<span data-ttu-id="55b79-299">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="55b79-299">COLUMN_DEF</span></span>|<span data-ttu-id="55b79-300">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-300">String</span></span>|  
|<span data-ttu-id="55b79-301">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="55b79-301">SQL_DATA_TYPE</span></span>|<span data-ttu-id="55b79-302">Int16</span><span class="sxs-lookup"><span data-stu-id="55b79-302">Int16</span></span>|  
|<span data-ttu-id="55b79-303">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="55b79-303">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="55b79-304">Int16</span><span class="sxs-lookup"><span data-stu-id="55b79-304">Int16</span></span>|  
|<span data-ttu-id="55b79-305">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="55b79-305">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="55b79-306">Int32</span><span class="sxs-lookup"><span data-stu-id="55b79-306">Int32</span></span>|  
|<span data-ttu-id="55b79-307">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="55b79-307">ORDINAL_POSITION</span></span>|<span data-ttu-id="55b79-308">Int32</span><span class="sxs-lookup"><span data-stu-id="55b79-308">Int32</span></span>|  
|<span data-ttu-id="55b79-309">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="55b79-309">IS_NULLABLE</span></span>|<span data-ttu-id="55b79-310">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-310">String</span></span>|  
|<span data-ttu-id="55b79-311">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="55b79-311">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="55b79-312">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-312">String</span></span>|  
|<span data-ttu-id="55b79-313">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="55b79-313">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="55b79-314">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-314">String</span></span>|  
|<span data-ttu-id="55b79-315">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="55b79-315">SS_DATA_TYPE</span></span>|<span data-ttu-id="55b79-316">Byte</span><span class="sxs-lookup"><span data-stu-id="55b79-316">Byte</span></span>|  
  
## <a name="microsoft-oracle-odbc-driver"></a><span data-ttu-id="55b79-317">Driver ODBC do Microsoft Oracle</span><span class="sxs-lookup"><span data-stu-id="55b79-317">Microsoft Oracle ODBC Driver</span></span>  
 <span data-ttu-id="55b79-318">O Driver ODBC do Microsoft SQL Server Oracle suporta as seguintes coleções de esquema específico, além das coleções de esquema comuns:</span><span class="sxs-lookup"><span data-stu-id="55b79-318">The Microsoft SQL Server Oracle ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="55b79-319">Tabelas</span><span class="sxs-lookup"><span data-stu-id="55b79-319">Tables</span></span>  
  
-   <span data-ttu-id="55b79-320">Colunas</span><span class="sxs-lookup"><span data-stu-id="55b79-320">Columns</span></span>  
  
-   <span data-ttu-id="55b79-321">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="55b79-321">Procedures</span></span>  
  
-   <span data-ttu-id="55b79-322">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="55b79-322">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="55b79-323">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="55b79-323">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="55b79-324">Exibições</span><span class="sxs-lookup"><span data-stu-id="55b79-324">Views</span></span>  
  
-   <span data-ttu-id="55b79-325">Índices</span><span class="sxs-lookup"><span data-stu-id="55b79-325">Indexes</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="55b79-326">Tabelas e exibições</span><span class="sxs-lookup"><span data-stu-id="55b79-326">Tables and Views</span></span>  
  
|<span data-ttu-id="55b79-327">ColumnName</span><span class="sxs-lookup"><span data-stu-id="55b79-327">ColumnName</span></span>|<span data-ttu-id="55b79-328">DataType</span><span class="sxs-lookup"><span data-stu-id="55b79-328">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="55b79-329">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="55b79-329">TABLE_QUALIFIER</span></span>|<span data-ttu-id="55b79-330">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-330">String</span></span>|  
|<span data-ttu-id="55b79-331">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="55b79-331">TABLE_OWNER</span></span>|<span data-ttu-id="55b79-332">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-332">String</span></span>|  
|<span data-ttu-id="55b79-333">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="55b79-333">TABLE_NAME</span></span>|<span data-ttu-id="55b79-334">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-334">String</span></span>|  
|<span data-ttu-id="55b79-335">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="55b79-335">TABLE_TYPE</span></span>|<span data-ttu-id="55b79-336">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-336">String</span></span>|  
|<span data-ttu-id="55b79-337">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="55b79-337">REMARKS</span></span>|<span data-ttu-id="55b79-338">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-338">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="55b79-339">Colunas</span><span class="sxs-lookup"><span data-stu-id="55b79-339">Columns</span></span>  
  
|<span data-ttu-id="55b79-340">ColumnName</span><span class="sxs-lookup"><span data-stu-id="55b79-340">ColumnName</span></span>|<span data-ttu-id="55b79-341">DataType</span><span class="sxs-lookup"><span data-stu-id="55b79-341">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="55b79-342">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="55b79-342">TABLE_QUALIFIER</span></span>|<span data-ttu-id="55b79-343">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-343">String</span></span>|  
|<span data-ttu-id="55b79-344">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="55b79-344">TABLE_OWNER</span></span>|<span data-ttu-id="55b79-345">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-345">String</span></span>|  
|<span data-ttu-id="55b79-346">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="55b79-346">TABLE_NAME</span></span>|<span data-ttu-id="55b79-347">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-347">String</span></span>|  
|<span data-ttu-id="55b79-348">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="55b79-348">COLUMN_NAME</span></span>|<span data-ttu-id="55b79-349">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-349">String</span></span>|  
|<span data-ttu-id="55b79-350">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="55b79-350">DATA_TYPE</span></span>|<span data-ttu-id="55b79-351">Int16</span><span class="sxs-lookup"><span data-stu-id="55b79-351">Int16</span></span>|  
|<span data-ttu-id="55b79-352">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="55b79-352">TYPE_NAME</span></span>|<span data-ttu-id="55b79-353">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-353">String</span></span>|  
|<span data-ttu-id="55b79-354">PRECISÃO</span><span class="sxs-lookup"><span data-stu-id="55b79-354">PRECISION</span></span>|<span data-ttu-id="55b79-355">Int32</span><span class="sxs-lookup"><span data-stu-id="55b79-355">Int32</span></span>|  
|<span data-ttu-id="55b79-356">COMPRIMENTO</span><span class="sxs-lookup"><span data-stu-id="55b79-356">LENGTH</span></span>|<span data-ttu-id="55b79-357">Int32</span><span class="sxs-lookup"><span data-stu-id="55b79-357">Int32</span></span>|  
|<span data-ttu-id="55b79-358">ESCALA</span><span class="sxs-lookup"><span data-stu-id="55b79-358">SCALE</span></span>|<span data-ttu-id="55b79-359">Int16</span><span class="sxs-lookup"><span data-stu-id="55b79-359">Int16</span></span>|  
|<span data-ttu-id="55b79-360">RADIX</span><span class="sxs-lookup"><span data-stu-id="55b79-360">RADIX</span></span>|<span data-ttu-id="55b79-361">Int16</span><span class="sxs-lookup"><span data-stu-id="55b79-361">Int16</span></span>|  
|<span data-ttu-id="55b79-362">PERMITE VALOR NULO</span><span class="sxs-lookup"><span data-stu-id="55b79-362">NULLABLE</span></span>|<span data-ttu-id="55b79-363">Int16</span><span class="sxs-lookup"><span data-stu-id="55b79-363">Int16</span></span>|  
|<span data-ttu-id="55b79-364">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="55b79-364">REMARKS</span></span>|<span data-ttu-id="55b79-365">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-365">String</span></span>|  
|<span data-ttu-id="55b79-366">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="55b79-366">ORDINAL_POSITION</span></span>|<span data-ttu-id="55b79-367">Int32</span><span class="sxs-lookup"><span data-stu-id="55b79-367">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="55b79-368">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="55b79-368">Procedures</span></span>  
  
|<span data-ttu-id="55b79-369">ColumnName</span><span class="sxs-lookup"><span data-stu-id="55b79-369">ColumnName</span></span>|<span data-ttu-id="55b79-370">DataType</span><span class="sxs-lookup"><span data-stu-id="55b79-370">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="55b79-371">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="55b79-371">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="55b79-372">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-372">String</span></span>|  
|<span data-ttu-id="55b79-373">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="55b79-373">PROCEDURE_OWNER</span></span>|<span data-ttu-id="55b79-374">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-374">String</span></span>|  
|<span data-ttu-id="55b79-375">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="55b79-375">PROCEDURE_NAME</span></span>|<span data-ttu-id="55b79-376">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-376">String</span></span>|  
|<span data-ttu-id="55b79-377">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="55b79-377">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="55b79-378">Int16</span><span class="sxs-lookup"><span data-stu-id="55b79-378">Int16</span></span>|  
|<span data-ttu-id="55b79-379">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="55b79-379">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="55b79-380">Int16</span><span class="sxs-lookup"><span data-stu-id="55b79-380">Int16</span></span>|  
|<span data-ttu-id="55b79-381">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="55b79-381">NUM_RESULT_SETS</span></span>|<span data-ttu-id="55b79-382">Int16</span><span class="sxs-lookup"><span data-stu-id="55b79-382">Int16</span></span>|  
|<span data-ttu-id="55b79-383">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="55b79-383">REMARKS</span></span>|<span data-ttu-id="55b79-384">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-384">String</span></span>|  
|<span data-ttu-id="55b79-385">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="55b79-385">PROCEDURE_TYPE</span></span>|<span data-ttu-id="55b79-386">Int16</span><span class="sxs-lookup"><span data-stu-id="55b79-386">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="55b79-387">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="55b79-387">ProcedureColumns</span></span>  
  
|<span data-ttu-id="55b79-388">ColumnName</span><span class="sxs-lookup"><span data-stu-id="55b79-388">ColumnName</span></span>|<span data-ttu-id="55b79-389">DataType</span><span class="sxs-lookup"><span data-stu-id="55b79-389">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="55b79-390">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="55b79-390">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="55b79-391">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-391">String</span></span>|  
|<span data-ttu-id="55b79-392">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="55b79-392">PROCEDURE_OWNER</span></span>|<span data-ttu-id="55b79-393">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-393">String</span></span>|  
|<span data-ttu-id="55b79-394">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="55b79-394">PROCEDURE_NAME</span></span>|<span data-ttu-id="55b79-395">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-395">String</span></span>|  
|<span data-ttu-id="55b79-396">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="55b79-396">COLUMN_NAME</span></span>|<span data-ttu-id="55b79-397">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-397">String</span></span>|  
|<span data-ttu-id="55b79-398">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="55b79-398">COLUMN_TYPE</span></span>|<span data-ttu-id="55b79-399">Int16</span><span class="sxs-lookup"><span data-stu-id="55b79-399">Int16</span></span>|  
|<span data-ttu-id="55b79-400">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="55b79-400">DATA_TYPE</span></span>|<span data-ttu-id="55b79-401">Int16</span><span class="sxs-lookup"><span data-stu-id="55b79-401">Int16</span></span>|  
|<span data-ttu-id="55b79-402">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="55b79-402">TYPE_NAME</span></span>|<span data-ttu-id="55b79-403">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-403">String</span></span>|  
|<span data-ttu-id="55b79-404">PRECISÃO</span><span class="sxs-lookup"><span data-stu-id="55b79-404">PRECISION</span></span>|<span data-ttu-id="55b79-405">Int32</span><span class="sxs-lookup"><span data-stu-id="55b79-405">Int32</span></span>|  
|<span data-ttu-id="55b79-406">COMPRIMENTO</span><span class="sxs-lookup"><span data-stu-id="55b79-406">LENGTH</span></span>|<span data-ttu-id="55b79-407">Int32</span><span class="sxs-lookup"><span data-stu-id="55b79-407">Int32</span></span>|  
|<span data-ttu-id="55b79-408">ESCALA</span><span class="sxs-lookup"><span data-stu-id="55b79-408">SCALE</span></span>|<span data-ttu-id="55b79-409">Int16</span><span class="sxs-lookup"><span data-stu-id="55b79-409">Int16</span></span>|  
|<span data-ttu-id="55b79-410">RADIX</span><span class="sxs-lookup"><span data-stu-id="55b79-410">RADIX</span></span>|<span data-ttu-id="55b79-411">Int16</span><span class="sxs-lookup"><span data-stu-id="55b79-411">Int16</span></span>|  
|<span data-ttu-id="55b79-412">PERMITE VALOR NULO</span><span class="sxs-lookup"><span data-stu-id="55b79-412">NULLABLE</span></span>|<span data-ttu-id="55b79-413">Int16</span><span class="sxs-lookup"><span data-stu-id="55b79-413">Int16</span></span>|  
|<span data-ttu-id="55b79-414">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="55b79-414">REMARKS</span></span>|<span data-ttu-id="55b79-415">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-415">String</span></span>|  
|<span data-ttu-id="55b79-416">SOBRECARGA</span><span class="sxs-lookup"><span data-stu-id="55b79-416">OVERLOAD</span></span>|<span data-ttu-id="55b79-417">Int32</span><span class="sxs-lookup"><span data-stu-id="55b79-417">Int32</span></span>|  
|<span data-ttu-id="55b79-418">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="55b79-418">ORDINAL_POSITION</span></span>|<span data-ttu-id="55b79-419">Int32</span><span class="sxs-lookup"><span data-stu-id="55b79-419">Int32</span></span>|  
  
## <a name="microsoft-jet-odbc-driver"></a><span data-ttu-id="55b79-420">Microsoft Jet ODBC Driver</span><span class="sxs-lookup"><span data-stu-id="55b79-420">Microsoft Jet ODBC Driver</span></span>  
 <span data-ttu-id="55b79-421">O Driver ODBC do Microsoft Jet suporta as seguintes coleções de esquema específico, além das coleções de esquema comuns:</span><span class="sxs-lookup"><span data-stu-id="55b79-421">The Microsoft Jet ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="55b79-422">Tabelas</span><span class="sxs-lookup"><span data-stu-id="55b79-422">Tables</span></span>  
  
-   <span data-ttu-id="55b79-423">Índices</span><span class="sxs-lookup"><span data-stu-id="55b79-423">Indexes</span></span>  
  
-   <span data-ttu-id="55b79-424">Colunas</span><span class="sxs-lookup"><span data-stu-id="55b79-424">Columns</span></span>  
  
-   <span data-ttu-id="55b79-425">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="55b79-425">Procedures</span></span>  
  
-   <span data-ttu-id="55b79-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="55b79-426">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="55b79-427">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="55b79-427">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="55b79-428">Exibições</span><span class="sxs-lookup"><span data-stu-id="55b79-428">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="55b79-429">Tabelas e exibições</span><span class="sxs-lookup"><span data-stu-id="55b79-429">Tables and Views</span></span>  
  
|<span data-ttu-id="55b79-430">ColumnName</span><span class="sxs-lookup"><span data-stu-id="55b79-430">ColumnName</span></span>|<span data-ttu-id="55b79-431">DataType</span><span class="sxs-lookup"><span data-stu-id="55b79-431">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="55b79-432">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="55b79-432">TABLE_QUALIFIER</span></span>|<span data-ttu-id="55b79-433">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-433">String</span></span>|  
|<span data-ttu-id="55b79-434">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="55b79-434">TABLE_OWNER</span></span>|<span data-ttu-id="55b79-435">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-435">String</span></span>|  
|<span data-ttu-id="55b79-436">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="55b79-436">TABLE_NAME</span></span>|<span data-ttu-id="55b79-437">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-437">String</span></span>|  
|<span data-ttu-id="55b79-438">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="55b79-438">TABLE_TYPE</span></span>|<span data-ttu-id="55b79-439">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-439">String</span></span>|  
|<span data-ttu-id="55b79-440">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="55b79-440">REMARKS</span></span>|<span data-ttu-id="55b79-441">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-441">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="55b79-442">Colunas</span><span class="sxs-lookup"><span data-stu-id="55b79-442">Columns</span></span>  
  
|<span data-ttu-id="55b79-443">ColumnName</span><span class="sxs-lookup"><span data-stu-id="55b79-443">ColumnName</span></span>|<span data-ttu-id="55b79-444">DataType</span><span class="sxs-lookup"><span data-stu-id="55b79-444">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="55b79-445">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="55b79-445">TABLE_QUALIFIER</span></span>|<span data-ttu-id="55b79-446">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-446">String</span></span>|  
|<span data-ttu-id="55b79-447">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="55b79-447">TABLE_OWNER</span></span>|<span data-ttu-id="55b79-448">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-448">String</span></span>|  
|<span data-ttu-id="55b79-449">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="55b79-449">TABLE_NAME</span></span>|<span data-ttu-id="55b79-450">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-450">String</span></span>|  
|<span data-ttu-id="55b79-451">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="55b79-451">COLUMN_NAME</span></span>|<span data-ttu-id="55b79-452">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-452">String</span></span>|  
|<span data-ttu-id="55b79-453">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="55b79-453">DATA_TYPE</span></span>|<span data-ttu-id="55b79-454">Int16</span><span class="sxs-lookup"><span data-stu-id="55b79-454">Int16</span></span>|  
|<span data-ttu-id="55b79-455">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="55b79-455">TYPE_NAME</span></span>|<span data-ttu-id="55b79-456">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-456">String</span></span>|  
|<span data-ttu-id="55b79-457">PRECISÃO</span><span class="sxs-lookup"><span data-stu-id="55b79-457">PRECISION</span></span>|<span data-ttu-id="55b79-458">Int32</span><span class="sxs-lookup"><span data-stu-id="55b79-458">Int32</span></span>|  
|<span data-ttu-id="55b79-459">COMPRIMENTO</span><span class="sxs-lookup"><span data-stu-id="55b79-459">LENGTH</span></span>|<span data-ttu-id="55b79-460">Int32</span><span class="sxs-lookup"><span data-stu-id="55b79-460">Int32</span></span>|  
|<span data-ttu-id="55b79-461">ESCALA</span><span class="sxs-lookup"><span data-stu-id="55b79-461">SCALE</span></span>|<span data-ttu-id="55b79-462">Int16</span><span class="sxs-lookup"><span data-stu-id="55b79-462">Int16</span></span>|  
|<span data-ttu-id="55b79-463">RADIX</span><span class="sxs-lookup"><span data-stu-id="55b79-463">RADIX</span></span>|<span data-ttu-id="55b79-464">Int16</span><span class="sxs-lookup"><span data-stu-id="55b79-464">Int16</span></span>|  
|<span data-ttu-id="55b79-465">PERMITE VALOR NULO</span><span class="sxs-lookup"><span data-stu-id="55b79-465">NULLABLE</span></span>|<span data-ttu-id="55b79-466">Int16</span><span class="sxs-lookup"><span data-stu-id="55b79-466">Int16</span></span>|  
|<span data-ttu-id="55b79-467">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="55b79-467">REMARKS</span></span>|<span data-ttu-id="55b79-468">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-468">String</span></span>|  
|<span data-ttu-id="55b79-469">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="55b79-469">ORDINAL_POSITION</span></span>|<span data-ttu-id="55b79-470">Int32</span><span class="sxs-lookup"><span data-stu-id="55b79-470">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="55b79-471">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="55b79-471">Procedures</span></span>  
  
|<span data-ttu-id="55b79-472">ColumnName</span><span class="sxs-lookup"><span data-stu-id="55b79-472">ColumnName</span></span>|<span data-ttu-id="55b79-473">DataType</span><span class="sxs-lookup"><span data-stu-id="55b79-473">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="55b79-474">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="55b79-474">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="55b79-475">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-475">String</span></span>|  
|<span data-ttu-id="55b79-476">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="55b79-476">PROCEDURE_OWNER</span></span>|<span data-ttu-id="55b79-477">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-477">String</span></span>|  
|<span data-ttu-id="55b79-478">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="55b79-478">PROCEDURE_NAME</span></span>|<span data-ttu-id="55b79-479">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-479">String</span></span>|  
|<span data-ttu-id="55b79-480">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="55b79-480">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="55b79-481">Int16</span><span class="sxs-lookup"><span data-stu-id="55b79-481">Int16</span></span>|  
|<span data-ttu-id="55b79-482">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="55b79-482">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="55b79-483">Int16</span><span class="sxs-lookup"><span data-stu-id="55b79-483">Int16</span></span>|  
|<span data-ttu-id="55b79-484">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="55b79-484">NUM_RESULT_SETS</span></span>|<span data-ttu-id="55b79-485">Int16</span><span class="sxs-lookup"><span data-stu-id="55b79-485">Int16</span></span>|  
|<span data-ttu-id="55b79-486">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="55b79-486">REMARKS</span></span>|<span data-ttu-id="55b79-487">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-487">String</span></span>|  
|<span data-ttu-id="55b79-488">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="55b79-488">PROCEDURE_TYPE</span></span>|<span data-ttu-id="55b79-489">Int16</span><span class="sxs-lookup"><span data-stu-id="55b79-489">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="55b79-490">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="55b79-490">ProcedureColumns</span></span>  
  
|<span data-ttu-id="55b79-491">ColumnName</span><span class="sxs-lookup"><span data-stu-id="55b79-491">ColumnName</span></span>|<span data-ttu-id="55b79-492">DataType</span><span class="sxs-lookup"><span data-stu-id="55b79-492">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="55b79-493">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="55b79-493">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="55b79-494">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-494">String</span></span>|  
|<span data-ttu-id="55b79-495">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="55b79-495">PROCEDURE_OWNER</span></span>|<span data-ttu-id="55b79-496">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-496">String</span></span>|  
|<span data-ttu-id="55b79-497">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="55b79-497">PROCEDURE_NAME</span></span>|<span data-ttu-id="55b79-498">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-498">String</span></span>|  
|<span data-ttu-id="55b79-499">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="55b79-499">COLUMN_NAME</span></span>|<span data-ttu-id="55b79-500">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-500">String</span></span>|  
|<span data-ttu-id="55b79-501">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="55b79-501">COLUMN_TYPE</span></span>|<span data-ttu-id="55b79-502">Int16</span><span class="sxs-lookup"><span data-stu-id="55b79-502">Int16</span></span>|  
|<span data-ttu-id="55b79-503">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="55b79-503">DATA_TYPE</span></span>|<span data-ttu-id="55b79-504">Int16</span><span class="sxs-lookup"><span data-stu-id="55b79-504">Int16</span></span>|  
|<span data-ttu-id="55b79-505">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="55b79-505">TYPE_NAME</span></span>|<span data-ttu-id="55b79-506">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-506">String</span></span>|  
|<span data-ttu-id="55b79-507">PRECISÃO</span><span class="sxs-lookup"><span data-stu-id="55b79-507">PRECISION</span></span>|<span data-ttu-id="55b79-508">Int32</span><span class="sxs-lookup"><span data-stu-id="55b79-508">Int32</span></span>|  
|<span data-ttu-id="55b79-509">COMPRIMENTO</span><span class="sxs-lookup"><span data-stu-id="55b79-509">LENGTH</span></span>|<span data-ttu-id="55b79-510">Int32</span><span class="sxs-lookup"><span data-stu-id="55b79-510">Int32</span></span>|  
|<span data-ttu-id="55b79-511">ESCALA</span><span class="sxs-lookup"><span data-stu-id="55b79-511">SCALE</span></span>|<span data-ttu-id="55b79-512">Int16</span><span class="sxs-lookup"><span data-stu-id="55b79-512">Int16</span></span>|  
|<span data-ttu-id="55b79-513">RADIX</span><span class="sxs-lookup"><span data-stu-id="55b79-513">RADIX</span></span>|<span data-ttu-id="55b79-514">Int16</span><span class="sxs-lookup"><span data-stu-id="55b79-514">Int16</span></span>|  
|<span data-ttu-id="55b79-515">PERMITE VALOR NULO</span><span class="sxs-lookup"><span data-stu-id="55b79-515">NULLABLE</span></span>|<span data-ttu-id="55b79-516">Int16</span><span class="sxs-lookup"><span data-stu-id="55b79-516">Int16</span></span>|  
|<span data-ttu-id="55b79-517">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="55b79-517">REMARKS</span></span>|<span data-ttu-id="55b79-518">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-518">String</span></span>|  
|<span data-ttu-id="55b79-519">SOBRECARGA</span><span class="sxs-lookup"><span data-stu-id="55b79-519">OVERLOAD</span></span>|<span data-ttu-id="55b79-520">Int32</span><span class="sxs-lookup"><span data-stu-id="55b79-520">Int32</span></span>|  
|<span data-ttu-id="55b79-521">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="55b79-521">ORDINAL_POSITION</span></span>|<span data-ttu-id="55b79-522">Int32</span><span class="sxs-lookup"><span data-stu-id="55b79-522">Int32</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="55b79-523">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="55b79-523">ProcedureParameters</span></span>  
  
|<span data-ttu-id="55b79-524">ColumnName</span><span class="sxs-lookup"><span data-stu-id="55b79-524">ColumnName</span></span>|<span data-ttu-id="55b79-525">DataType</span><span class="sxs-lookup"><span data-stu-id="55b79-525">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="55b79-526">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="55b79-526">PROCEDURE_CAT</span></span>|<span data-ttu-id="55b79-527">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-527">String</span></span>|  
|<span data-ttu-id="55b79-528">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="55b79-528">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="55b79-529">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-529">String</span></span>|  
|<span data-ttu-id="55b79-530">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="55b79-530">PROCEDURE_NAME</span></span>|<span data-ttu-id="55b79-531">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-531">String</span></span>|  
|<span data-ttu-id="55b79-532">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="55b79-532">COLUMN_NAME</span></span>|<span data-ttu-id="55b79-533">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-533">String</span></span>|  
|<span data-ttu-id="55b79-534">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="55b79-534">COLUMN_TYPE</span></span>|<span data-ttu-id="55b79-535">Int16</span><span class="sxs-lookup"><span data-stu-id="55b79-535">Int16</span></span>|  
|<span data-ttu-id="55b79-536">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="55b79-536">DATA_TYPE</span></span>|<span data-ttu-id="55b79-537">Int16</span><span class="sxs-lookup"><span data-stu-id="55b79-537">Int16</span></span>|  
|<span data-ttu-id="55b79-538">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="55b79-538">TYPE_NAME</span></span>|<span data-ttu-id="55b79-539">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-539">String</span></span>|  
|<span data-ttu-id="55b79-540">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="55b79-540">COLUMN_SIZE</span></span>|<span data-ttu-id="55b79-541">Int32</span><span class="sxs-lookup"><span data-stu-id="55b79-541">Int32</span></span>|  
|<span data-ttu-id="55b79-542">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="55b79-542">BUFFER_LENGTH</span></span>|<span data-ttu-id="55b79-543">Int32</span><span class="sxs-lookup"><span data-stu-id="55b79-543">Int32</span></span>|  
|<span data-ttu-id="55b79-544">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="55b79-544">DECIMAL_DIGITS</span></span>|<span data-ttu-id="55b79-545">Int16</span><span class="sxs-lookup"><span data-stu-id="55b79-545">Int16</span></span>|  
|<span data-ttu-id="55b79-546">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="55b79-546">NUM_PREC_RADIX</span></span>|<span data-ttu-id="55b79-547">Int16</span><span class="sxs-lookup"><span data-stu-id="55b79-547">Int16</span></span>|  
|<span data-ttu-id="55b79-548">PERMITE VALOR NULO</span><span class="sxs-lookup"><span data-stu-id="55b79-548">NULLABLE</span></span>|<span data-ttu-id="55b79-549">Int16</span><span class="sxs-lookup"><span data-stu-id="55b79-549">Int16</span></span>|  
|<span data-ttu-id="55b79-550">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="55b79-550">REMARKS</span></span>|<span data-ttu-id="55b79-551">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-551">String</span></span>|  
|<span data-ttu-id="55b79-552">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="55b79-552">COLUMN_DEF</span></span>|<span data-ttu-id="55b79-553">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-553">String</span></span>|  
|<span data-ttu-id="55b79-554">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="55b79-554">SQL_DATA_TYPE</span></span>|<span data-ttu-id="55b79-555">Int16</span><span class="sxs-lookup"><span data-stu-id="55b79-555">Int16</span></span>|  
|<span data-ttu-id="55b79-556">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="55b79-556">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="55b79-557">Int16</span><span class="sxs-lookup"><span data-stu-id="55b79-557">Int16</span></span>|  
|<span data-ttu-id="55b79-558">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="55b79-558">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="55b79-559">Int32</span><span class="sxs-lookup"><span data-stu-id="55b79-559">Int32</span></span>|  
|<span data-ttu-id="55b79-560">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="55b79-560">ORDINAL_POSITION</span></span>|<span data-ttu-id="55b79-561">Int32</span><span class="sxs-lookup"><span data-stu-id="55b79-561">Int32</span></span>|  
|<span data-ttu-id="55b79-562">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="55b79-562">IS_NULLABLE</span></span>|<span data-ttu-id="55b79-563">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="55b79-563">String</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="55b79-564">Consulte também</span><span class="sxs-lookup"><span data-stu-id="55b79-564">See Also</span></span>  
 <span data-ttu-id="55b79-565">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="55b79-565">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
