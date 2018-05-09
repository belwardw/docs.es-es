### <a name="resizing-a-grid-can-hang"></a><span data-ttu-id="0cbc4-101">El cambio de tamaño de una cuadrícula puede dejar de responder</span><span class="sxs-lookup"><span data-stu-id="0cbc4-101">Resizing a Grid can hang</span></span>

|   |   |
|---|---|
|<span data-ttu-id="0cbc4-102">Detalles</span><span class="sxs-lookup"><span data-stu-id="0cbc4-102">Details</span></span>|<span data-ttu-id="0cbc4-103">Se puede producir un bucle infinito durante el diseño de un control <code>T:System.Windows.Controls.Grid</code> en las siguientes circunstancias:</span><span class="sxs-lookup"><span data-stu-id="0cbc4-103">An infinite loop can occur during layout of a <code>T:System.Windows.Controls.Grid</code> under the following circumstances:</span></span><ul><li><span data-ttu-id="0cbc4-104">Las definiciones de fila contienen dos filas \*, que declaran un valor MinHeight y un valor MaxHeight.</span><span class="sxs-lookup"><span data-stu-id="0cbc4-104">Row definitions contain two \*-rows, both declaring a MinHeight and a MaxHeight.</span></span></li><li><span data-ttu-id="0cbc4-105">El contenido de las filas \* no supera el valor MaxHeight correspondiente.</span><span class="sxs-lookup"><span data-stu-id="0cbc4-105">Content of the \*-rows doesn't exceed the corresponding MaxHeight</span></span></li><li><span data-ttu-id="0cbc4-106">El alto disponible de la cuadrícula se supera con el primer valor MinHeight (más cualquier otra fila fija o automática).</span><span class="sxs-lookup"><span data-stu-id="0cbc4-106">The Grid's available height is exceeded by the first MinHeight (plus any other fixed or Auto rows)</span></span></li><li><span data-ttu-id="0cbc4-107">La aplicación tiene como destino .NET 4.7 o admite el algoritmo de asignación de .NET 4.7 estableciendo <code>Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=false</code>.</span><span class="sxs-lookup"><span data-stu-id="0cbc4-107">The app targets .Net 4.7, or opts in to the 4.7 allocation algorithm by setting <code>Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=false</code></span></span></li></ul><span data-ttu-id="0cbc4-108">El bucle también se podría producir con más de dos filas o en el mismo caso para las columnas. El problema se ha corregido en .NET 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="0cbc4-108">The loop would also happen with more than two rows, or in the analogous case for columns.The issue is fixed in .Net 4.7.1.</span></span>|
|<span data-ttu-id="0cbc4-109">Sugerencia</span><span class="sxs-lookup"><span data-stu-id="0cbc4-109">Suggestion</span></span>|<span data-ttu-id="0cbc4-110">Actualice a .NET 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="0cbc4-110">Upgrade to .Net 4.7.1.</span></span>  <span data-ttu-id="0cbc4-111">Como alternativa, si ya no necesita el algoritmo de asignación de la versión 4.7, puede usar la opción de configuración siguiente:</span><span class="sxs-lookup"><span data-stu-id="0cbc4-111">Alternatively, if you don't need the 4.7 allocation algorithm you can use the following configuration setting:</span></span><pre><code class="language-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="0cbc4-112">Ámbito</span><span class="sxs-lookup"><span data-stu-id="0cbc4-112">Scope</span></span>|<span data-ttu-id="0cbc4-113">Borde</span><span class="sxs-lookup"><span data-stu-id="0cbc4-113">Edge</span></span>|
|<span data-ttu-id="0cbc4-114">Versión</span><span class="sxs-lookup"><span data-stu-id="0cbc4-114">Version</span></span>|<span data-ttu-id="0cbc4-115">4.7</span><span class="sxs-lookup"><span data-stu-id="0cbc4-115">4.7</span></span>|
|<span data-ttu-id="0cbc4-116">Tipo</span><span class="sxs-lookup"><span data-stu-id="0cbc4-116">Type</span></span>|<span data-ttu-id="0cbc4-117">Tiempo de ejecución</span><span class="sxs-lookup"><span data-stu-id="0cbc4-117">Runtime</span></span>|
