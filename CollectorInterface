import java.util.*;
import java.util.function.*;

import java.util.stream.Collector;
import java.util.stream.Collectors;

public class CollectorInterface {
    public static void main(String[] args) {
        List<String> words = Arrays.asList("apple", "banana", "cherry", "date");

        // Using the custom collector
        String result = words.stream()
                .collect(toStringCollector());
        System.out.println(result); // Output: apple,banana,cherry,date
    }

    public static <T> Collector<T, StringBuilder, String> toStringCollector() {
        return new Collector<T, StringBuilder, String>() {

            // 1. Supplier: Creates an empty StringBuilder as the initial container.
            @Override
            public Supplier<StringBuilder> supplier() {
                return StringBuilder::new; // Returns a new StringBuilder instance
            }

            // 2. Accumulator: Appends each element of the stream to the StringBuilder.
            @Override
            public BiConsumer<StringBuilder, T> accumulator() {
                return (sb, t) -> {
                    if (sb.length() > 0) {
                        sb.append(","); // Add a separator if it's not the first element
                    }
                    sb.append(t.toString());
                };
            }

            // 3. Combiner: Combines two StringBuilder objects into one.
            @Override
            public BinaryOperator<StringBuilder> combiner() {
                return (sb1, sb2) -> sb1.append(sb2); // Appends the second StringBuilder to the first
            }

            // 4. Finisher: Converts the final StringBuilder to a String.
            @Override
            public Function<StringBuilder, String> finisher() {
                return StringBuilder::toString; // Converts StringBuilder to a String
            }

            // 5. Characteristics: This collector is unordered and does not support concurrent processing.
            @Override
            public Set<Collector.Characteristics> characteristics() {
                return EnumSet.of(Collector.Characteristics.UNORDERED);
            }
        };
    }
}
