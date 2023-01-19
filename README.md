# TDD_baseBallGame
TDD_Toy_Project : BaseBall Game



1. 요구사항
    - 먼저 1-9까지 서로 다른 3개의 숫자를 뽑는다. (랜덤)
    - 사용자에게 1-9까지 3개의 서로 다른 숫자들을 입력 받는다.
    - 임의로 만들어진 숫자 3개와 사용자가 입력한 숫자 3개를 비교한다.
    - 비교 결과를 사용자에게 보여 준다.

2. 클래스
    - BaseBallMain : 게임 실행 main
    - BaseballGame : run // 랜덤 숫자 생성 // 결과 변환/출력
    - CalculateBalls : 결과 계산
    - UserBallsGenerator : 사용자 입력

3. 테스트 코드 작성 순서
    - input의 숫자가 서로 다른 숫자인가
    - input의 숫자가 3자리인가
    - 1-9인가
	=> 랜덤 숫자 생성기 or 사용자 입력기

(랜덤 숫자 생성 메소드/결과 출력 메소드)
    - 3개
    - 서로다른 숫자
    - 1-9
    - String 타입으로 잘 출력됐는가
(숫자 비교 메소드)
    - Ball : 같은 수가 있는가, 몇개?
    - Strike : 그 숫자가 같은 자리에 있는가, 몇개?
(사용자 입력 메소드)
    - 3개
    - 서로다른 숫자
    - 1-9


4. 실제 TDD 작성 순서
	1) 프로그램이 잘 실행 되는가 : isGameCreated
	2) null이 아니고 3개가 맞는가 : isNotNullAnd3Num
	3) 1-9까지 숫자로 이루어졌는가 : isAllLettersOnlyHaveNumber1to9
	4) 중복이 없는가 : isAllLettersDifferent
	5) 유저 input (UserBallsGeneratorTest)
		* 5-1) isNotNullAnd3Num => isInput3Num, isRandomBall3Num
		* 5-2) isAllLettersOnlyHaveNumber1to9
		* 5-3) isAllLettersDifferent : 서로다른 숫자로 이루어졌는가
		* 5-4) isValid : input 조건 check 문제 없는가
		- input 받기
	6) 계산기
		* 6-1) strike (getStrikeCnt)
			- 3개가 모두 같을때 : is3StrikesWhenAllSame
			- 2개가 같을때 : is2StrikesWhenTwoNumberIsSame
			- 1개가 같을때 : is1StrikesWhenOneNumberIsSame
			==> 리팩토링 : isStrikeCntCorrect
		* 6-2) ball (getBallCnt)
			- 0개 : is0BallsWhenNoSameNum
			- 1개 : is1BallsWhenOneNumIsSame
			- 2개 : is2BallsWhenTwoNumIsSame
			- 3개 : is3BallsWhenThreeNumIsSame
			==> 리팩토링 : isBallCntCorrect
		* 6-3) strikes & balls 결과(getStrikeAndBallCnt) : isCntResultCorrect
	7) 결과 텍스트 출력
		* 7-1) nothing : isResultConvertNothing
		* 7-2) strike : isResultConvertStrike
		* 7-3) balls : isResultConvertBall
		* 7-4) strike&ball : isResultConvertStrikeAndBall
		==> 리팩토링 : isResultConvertCorrect
