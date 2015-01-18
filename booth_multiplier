----------------------------------------------------------------------------------
-- Company: 
-- Engineer: 
-- 
-- Create Date:    19:41:25 11/03/2013 
-- Design Name: 
-- Module Name:    booth - Behavioral 
-- Project Name: 
-- Target Devices: 
-- Tool versions: 
-- Description: 
--
-- Dependencies: 
--
-- Revision: 
-- Revision 0.01 - File Created
-- Additional Comments: 
--
----------------------------------------------------------------------------------
library IEEE;
use IEEE.STD_LOGIC_1164.ALL;
use IEEE.STD_LOGIC_ARITH.ALL;
use IEEE.STD_LOGIC_UNSIGNED.ALL;

-- Uncomment the following library declaration if using
-- arithmetic functions with Signed or Unsigned values
--use IEEE.NUMERIC_STD.ALL;

-- Uncomment the following library declaration if instantiating
-- any Xilinx primitives in this code.
--library UNISIM;
--use UNISIM.VComponents.all;

entity booth is
    Port ( m : in  STD_LOGIC_VECTOR (6 downto 0);
           r : in  STD_LOGIC_VECTOR (6 downto 0);
           product : out  STD_LOGIC_VECTOR (13 downto 0);
			  clk: in STD_LOGIC;
			  X_in : in  STD_LOGIC_VECTOR (15 downto 0);
			  Y_in : in  STD_LOGIC_VECTOR (15 downto 0);
			  Z_out : out  STD_LOGIC_VECTOR (15 downto 0);
			  func_in : in  STD_LOGIC_VECTOR (2 downto 0));
end booth;

architecture Behavioral of booth is
--Define the alu component
	COMPONENT alu
	PORT(
		X : IN std_logic_vector(15 downto 0);
		Y : IN std_logic_vector(15 downto 0);
		func : IN std_logic_vector(2 downto 0);          
		Z : OUT std_logic_vector(15 downto 0)
		);
	END COMPONENT;
--Registers for Booth Multiplier
signal A: std_logic_vector (15 downto 0);
signal S: std_logic_vector (15 downto 0);
signal P: std_logic_vector (15 downto 0);
begin
--Instantiate the alu
	Inst_alu: alu PORT MAP(
		X => X_in,
		Y => Y_in,
		Z => Z_out,
		func => func_in
	);
	process (m, r, Z, A, S, P, func, clk, X_in, Y_in, Z_out) begin
		--A <= (A(15 downto 9) =>  m(6 downto 0), others => '0');
		--A(15 downto 9) <= m(6 downto 0);
		--A(9 downto 0) <= 0;
		A <= m(6 downto 0) & (others => '0');
		P(7 downto 1) <= r(6 downto 0);
		P(15 downto 8) <= "0";
		P(0) <= '0';
		X_in(15 downto 9) => m(6 downto 0);
		func_in => "011";
		S(15 downto 9) <= Z_out(15 downto 9);
		
		S <= (S(15 downto 9) => not m + 1(6 downto 0) , others = '0');
			for i in 7 downto 1 loop
				if P(0) = 1 and P(1) = 0 then
				X_in <= A;
				Y_in <= P;
				func = "000";
				P <= Z_out;
				X_in <= P;
				func = "010"
				P => Z_out;
				elsif P(0) = 0 and P(1) = 1 then
				
				end if;
			end loop;


end Behavioral;

