<script lang="ts">
    const primes = [2, 3, 5, 7, 11, 13, 17, 19, 23, 29, 31, 37, 41, 43, 47, 53, 59, 61, 67, 71, 73, 79, 83, 89, 97]
    var countLambdas = 4;
    $: restKlassenRingOrdnung = rkrExponent**primeBasis;
    var primeBasis = 1;
    var rkrExponent = 7;
    $: lambdas = generateLambdas(restKlassenRingOrdnung, countLambdas)


function generateLambdas(restKlassenRingOrdnung: number,countLambdas: number): number[] {
    var toReturn: number[] = []
    for (var i = 0; i < countLambdas; i++){
        toReturn.push(i+1)
    }
    return toReturn;
}
</script>

<div>


    <h2>Reed Solomon Codes</h2>
    <h3>Parameter auswahl</h3>

    <div class="flex flex-row space-x-4">
        <div>Anzahl Lambdas</div>
        <div>
            <input type="number" min="2" max="20" bind:value={countLambdas}>
        </div>
        <div></div>
        {#each lambdas as lambda,i}
        <div>λ<sub>{i+1}</sub> =</div>
        <input class="w-12" type="number" bind:value={lambdas[i]}>
        {/each}
    </div>

    <div class="flex flex-row space-x-4">
        
        <div>
            Ordnung Restklassenring
        </div>
        <div>
            <select bind:value={rkrExponent}> 
                    {#each primes as prime,i}
                    <option value="{prime}">{prime}</option>
                    {/each}
            </select>
        </div>
        <div>hoch</div>
        <input type="number" bind:value={primeBasis} min=1 max=100>
        <div>
           ergibt 𝔽<sub>{restKlassenRingOrdnung}</sub>
        </div>
    </div>
</div>


<style lang="postcss">
    .flex{
        margin-bottom: 20px;
    }
</style>