# PhysicalExamination
# 자바를 활용한 클래스 배열에서 평균 키와 시력의 분포 구하기
생성자를 통해 이름, 키, 시력을 전달받습니다.

![화면 캡처 2023-03-17 09575](https://user-images.githubusercontent.com/126844596/225800114-8ec49119-fc75-43dd-901f-c4a53a143164.png)
PhysicDate 의 클래스로 부터 생선된 배열을 매개변수를 통해 전달받아 평균 키를 구하는 함수입니다.
![화면 캡처 2023-03-17 115700](https://user-images.githubusercontent.com/126844596/225802486-357dbad1-6e71-4a28-a92a-27b2d26a6ba2.png)









package sungil13;
class PhysicalExamination {

	static final int VMAX = 21;
	static class  PhyscData{
		String name;
		int height;
		double vision;
		
		PhyscData(String name, int height, double vision) {
			this.name = name;
			this.height = height;
			this.vision = vision;
		}
	}
	static double aveHeight(PhyscData[] dat) {
		double sum = 0;
		
		for(int i = 0; i< dat.length; i++) 
			sum += dat[i].height;
			
		return sum / dat.length;    }
		
	static void distVision(PhyscData[] dat, int[] dist) {
		int i = 0;
		dist[i]=0;
		for(i=0; i<dat.length;i++)
			if (dat[i].vision >= 0.0 && dat[i].vision<=VMAX / 10)
				dist[(int)(dat[i].vision * 10)]++;
	}
	 public static void main(String[] args) {

		 PhyscData[] x = {
				 new PhyscData("강민하", 162, 0.3),
				 new PhyscData("김찬우", 173, 0.7),
				 new PhyscData("박준서", 175, 2.0),
				 new PhyscData("유서범", 171, 1.5),
				 new PhyscData("이수연", 168, 0.4),
				 new PhyscData("장경오", 174, 1.2),
				 new PhyscData("황지안", 169, 0.8),
		 };
		 int[] vdist = new int[VMAX];
		 
		 System.out.println("■ 신체검사 리스트 ■");
		 System.out.println(" 이름       키    시력");
		 System.out.println("-----------------");
		 for (int i = 0; i< x.length; i++)
			 System.out.printf("%-6s%3d%5.1f\n", x[i].name, x[i].height, x[i].vision);
		 
		 System.out.printf("\n평균 키: %5.1fcm\n", aveHeight(x));
		 distVision(x, vdist);
		 System.out.println("\n시력분포");
		 for (int i = 0; i< VMAX; i++)	
			 System.out.printf("%3.1f ~ : %2d명\n", i / 10.0, vdist[i]);
	 }
	 
}




