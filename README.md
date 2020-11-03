This java library solves cutting stock problem using greedy approach.
Greedy approach may not give the optimal solution but gives an acceptable solution quickly.
Using this library is simple.

Here is a simple example

If I have metal rods of size 700mm and I want to cut it into pieces of different sizes suppose 700,500,250 and 380.
And I want pieces example

	700(mm) * 4 pieces
	500(mm) * 3 pieces
	250(mm) * 6 pieces
	320(mm) * 5 pieces
To cut this efficiently by minimizing the waste, here is the code.

Java Code
------------------------------------------------------
	import java.util.Map;
	import java.util.Map.Entry;
	import org.optimization.CuttingStock;
	
	public class MainClass {

		public static void main(String[] args) {

			int blocks[]={700,500,250,380};
			int quantities[]={4,3,6,5};
			int i=0,max_size=2000;
			Map<Integer, Integer> map;
		    CuttingStock cuttingStock= new CuttingStock(max_size,blocks,quantities);
			while(cuttingStock.hasMoreCombinations())
			{
				System.out.println("\nCombination no "+(++i));
				map=cuttingStock.nextCombination();
				for (Entry<Integer, Integer> entry : map.entrySet()) 
				{
					  Integer key = entry.getKey();
					  Integer value = entry.getValue();
					  System.out.println(key+"  *  "+value);
				}
			}
		}
	}


------------------------------------------------------
Output will be
------------------------------------------------------
	Combination no 1
	250  *  6
	500  *  1

	Combination no 2
	700  *  1
	500  *  1
	380  *  2

	Combination no 3
	700  *  1
	500  *  1
	380  *  2

	Combination no 4
	700  *  2
	380  *  1
------------------------------------------------------
